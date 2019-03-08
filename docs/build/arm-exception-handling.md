---
title: Control de excepciones de ARM
ms.date: 07/11/2018
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
ms.openlocfilehash: f6df8afd453f7e71d1ecc2ebb188c079a3aad02a
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694353"
---
# <a name="arm-exception-handling"></a>Control de excepciones de ARM

Windows en ARM emplea el mismo mecanismo de control de excepciones estructurado tanto en las excepciones generadas por hardware asincrónicas como en las excepciones generadas por software sincrónicas. Los controladores de excepciones específicos de lenguaje se basan en el control de excepciones estructurado de Windows por medio de funciones del asistente de lenguaje. Este documento describe el control de excepciones en Windows en ARM y las aplicaciones auxiliares de lenguaje utilizadas por el código generado por el ensamblador de ARM Microsoft y el compilador de Visual C++.

## <a name="arm-exception-handling"></a>Control de excepciones de ARM

Windows en ARM usa *códigos de desenredado* para controlar el desenredo de pila durante [control estructurado de excepciones](/windows/desktop/debug/structured-exception-handling) (SEH). Los códigos de desenredado son una secuencia de bytes almacenada en la sección .xdata de la imagen ejecutable. Describen la operación del código de prólogo y epílogo de la función de forma abstracta, ya que así los efectos del prólogo de una función se pueden deshacer como preparación para desenredar en el marco de pila del llamador.

La EABI de ARM especifica un modelo de desenredado en excepciones en el que se usan códigos de desenredado, pero esta especificación no basta para el desenredado SEH en Windows, donde se deben controlar casos asincrónicos en los que el procesador se encuentra en medio del prólogo y el epílogo de una función. Además, Windows divide el control de desenredado en desenredado en el nivel de función y desenredado de ámbito específico de lenguaje, algo que está unificado en la EABI de ARM. Por ello, Windows en ARM especifica más detalles para el procedimiento y los datos de desenredado.

### <a name="assumptions"></a>Suposiciones

Las imágenes ejecutables de Windows en ARM usan el formato portable ejecutable (PE). Para obtener más información, consulte [especificación Microsoft PE y COFF](http://go.microsoft.com/fwlink/p/?linkid=84140). La información de control de excepciones se almacena en las secciones .pdata y .xdata de la imagen.

En el mecanismo de control de excepciones se dan algunas cosas por hecho en relación con el código que sigue la ABI para Windows en ARM:

- Cuando se produce una excepción dentro del cuerpo de una función, no importa si las operaciones del prólogo se deshacen o si las operaciones del epílogo se llevan a cabo de forma avanzada. Ambas deberían generar idénticos resultados.

- Los prólogos y epílogos tienden a reflejarse entre sí, lo cual puede servir para reducir el tamaño de los metadatos que se necesitan para describir el desenredado.

- Las funciones tienden a ser relativamente pequeñas. Algunas optimizaciones se sirven de ello para empaquetar datos eficazmente.

- Si una condición se coloca en un epílogo, se aplica igualmente a todas las instrucciones de dicho epílogo.

- Si el puntero de pila (SP) se guarda en otro registro del prólogo, dicho registro debe permanecer inalterado durante toda la función, ya que así el SP original podrá recuperarse en cualquier momento.

- A menos que el SP se guarde en otro registro, cualquier manipulación que se le realice debe tener lugar estrictamente dentro del prólogo y el epílogo.

- Para desenredar un marco de pila, se necesitan las siguientes acciones:

  - Ajustar r13 (SP) en incrementos de 4 bytes.

  - Extraer uno o más registros de enteros.

  - Extraer uno o más registros de VFP (punto flotante virtual).

  - Copiar un valor de registro arbitrario en r13 (SP).

  - Cargar el SP de una pila mediante una operación de postdecremento pequeño.

  - Analizar alguno de los tipos de marco bien definidos.

### <a name="pdata-records"></a>Registros .pdata

Los registros .pdata en una imagen con formato PE consisten en una matriz ordenada de elementos de longitud fija que describen cada función de manipulación de la pila. Las funciones de hoja (que son funciones que no llaman a otras funciones) no precisan de registros .pdata cuando no manipulan la pila; dicho de otro modo, no necesitan un almacenamiento local ni guardar o restaurar registros no volátiles. Los registros de estas funciones se pueden omitir de la sección .pdata para ahorrar espacio. Una operación de desenredado de una de estas funciones puede simplemente copiar la dirección de devolución del registro de vínculo (LR) en el contador de programas (PC) para subir al llamador.

Cada registro .pdata de ARM tiene 8 bytes de longitud. El formato general de un registro coloca la dirección virtual relativa (RVA) del inicio de la función en la primera palabra de 32 bits, seguida de una segunda palabra que contiene o el puntero de un bloque .xdata de longitud variable, o una palabra empaquetada que describe una secuencia de desenredado de función canónica, como se indica en la siguiente tabla:

|Desplazamiento de palabra|Bits|Finalidad|
|-----------------|----------|-------------|
|0|0-31|*Función iniciar RVA* es la RVA de 32 bits del inicio de la función. Si la función contiene código Thumb, se debe establecer el bit inferior de esta dirección.|
|1|0-1|*Marca* es un campo de 2 bits que indica cómo interpretar los 30 bits restantes de la segunda palabra .pdata. Si *marca* es 0, a continuación, el resto de bits forma un *RVA de información de excepción* (con los dos bits inferiores implícitamente en 0). Si *marca* es distinto de cero, a continuación, el resto de bits forma un *datos de desenredado empaquetado* estructura.|
|1|2-31|*Información de excepción RVA* o *empaquetan datos de desenredo*.<br /><br /> *RVA de información de excepción* es la dirección de la estructura de información de excepción de longitud variable almacenada en la sección .xdata. Estos datos deben tener una alineación de 4 bytes.<br /><br /> *Empaqueta los datos de desenredo* es una descripción comprimida de las operaciones necesarias para desenredar desde una función, suponiendo que la forma canónica. En este caso, no se necesita un registro .xdata.|

### <a name="packed-unwind-data"></a>Datos de desenredado empaquetados

Se pueden usar datos de desenredado empaquetado en las funciones cuyos prólogos y epílogos sigan el formato canónico descrito a continuación. Esto hace que ya no sea necesario un registro .xdata, al tiempo que reduce notablemente el espacio necesario para proporcionar datos de desenredado. Los prólogos y epílogos canónicos están diseñados para cumplir los requisitos comunes de una función sencilla que no necesita un controlador de excepciones y que lleva a cabo sus operaciones de configuración y destrucción en el orden establecido.

En esta tabla se indica el formato de un registro .pdata que tiene datos de desenredado empaquetado:

|Desplazamiento de palabra|Bits|Finalidad|
|-----------------|----------|-------------|
|0|0-31|*Función iniciar RVA* es la RVA de 32 bits del inicio de la función. Si la función contiene código Thumb, se debe establecer el bit inferior de esta dirección.|
|1|0-1|*Marca* es un campo de 2 bits que tiene los siguientes significados:<br /><br />-00 = empaquetada desenredar datos no utilizados; Seleccione un registro .xdata bits restantes.<br />-01 = empaquetada datos de desenredo.<br />-10 = empaquetada datos donde se supone que la función carece de prólogo de desenredado. Esto resulta práctico a la hora de describir fragmentos de la función que no son contiguas al inicio de la función.<br />-11 = reservado.|
|1|2-12|*Función longitud* es un campo de 11 bits que proporciona la longitud de toda la función en bytes dividida entre 2. Si la función supera los 4000 bytes, se deberá usar en su lugar un registro .xdata.|
|1|13-14|*RET* es un campo de 2 bits que indica cómo devuelve la función:<br /><br />-00 = devolución mediante extracción {pc} (el *L* bit de marca debe establecerse en 1 en este caso).<br />-01 = devolución mediante una bifurcación de 16 bits.<br />-10 = devolución mediante una bifurcación de 32 bits.<br />-11 = no hay epílogo en absoluto. Esto resulta práctico a la hora de describir un fragmento de función no contiguo que solo puede contener un prólogo, pero cuyo epílogo puede estar en cualquier otra parte.|
|1|15|*H* es una marca de 1 bit que indica si la función "alberga" el parámetro entero registra (r0-r3) insertándolos al principio de la función y desasigna los 16 bytes de la pila antes de devolver. (0 = no alberga registros, 1 = alberga registros).|
|1|16-18|*Reg* se guarda de un campo de 3 bits que indica el índice del último registro no volátil. Si el *R* bit es 0, a continuación, solo los registros de enteros se guardan y se supone que en el intervalo r4-RN, donde N es igual a 4 + *Reg*. Si el *R* bit es 1, a continuación, registros de punto flotante solo se guardan y se supone que en el intervalo d8-DN, donde N es igual a 8 + *Reg*. La combinación especial de *R* = 1 y *Reg* = 7 indica que no se guardan registros.|
|1|19|*R* es una marca de 1 bit que indica si los registros no volátiles guardados son registros de tipo entero (0) o registros de punto flotante (1). Si *R* está establecido en 1 y el *Reg* campo se establece en 7, no se insertan ningún registros no volátiles.|
|1|20|*L* es una marca de 1 bit que indica si la función guarda/restaura LR, junto con otros registros especificados por el *Reg* campo. (0 = no guarda/restaura, 1 = guarda/restaura).|
|1|21|*C* es una marca de 1 bit que indica si la función incluye instrucciones adicionales para configurar una cadena de marcos de pila rápidos caminar (1) o no (0). Si este bit se establece, r11 se agrega implícitamente a la lista de registros no volátiles de enteros guardados (Vea a continuación si las restricciones de la *C* marca se usa.)|
|1|22-31|*Ajustar la pila* es un campo de 10 bits que indica el número de bytes de la pila que se asignan a esta función, dividida entre 4. Con todo, solo se pueden codificar directamente los valores comprendidos entre 0x000-0x3F3. Las funciones que asignan más de 4044 bytes de la pila deben usar un registro .xdata completo. Si el *ajuste de pila* campo es 0x3F4 o superior, los 4 bits inferiores tienen un significado especial:<br /><br />-Bits 0-1 indican el número de palabras del ajuste de pila (1-4) menos 1.<br />-2 bit se establece en 1 si el prólogo combinó este ajuste en su operación de inserción.<br />-3 bit se establece en 1 si el epílogo combinó este ajuste en su operación de extracción.|

Existen las siguientes restricciones, dada las posibles redundancias que se pueden producir en las codificaciones anteriores:

- Si el *C* marca se establece en 1:

   - El *L* marca también debe establecerse en 1, porque el encadenamiento de marcos requería tanto r11 como LR.

   - R11 no debe incluirse en el conjunto de registros descrito por *Reg*. Es decir, si se inserta r4 a r11, *Reg* solo deberá describir de r4 a r10, ya que el *C* marca implica r11.

- Si el *Ret* campo se establece en 0, el *L* marca debe establecerse en 1.

Si no se respetan estas restricciones, se generará una secuencia incompatible.

Para fines de la explicación siguiente, se derivan dos seudomarcas *ajuste de pila*:

- *PF* o "plegamiento de prólogo" indica que *ajuste de pila* es 0x3F4 o mayor y que el bit 2 está establecido.

- *EF* o "plegamiento de epílogo" indica que *ajuste de pila* es 0x3F4 o mayor y que el bit 3 está establecido.

Los prólogos para las funciones canónicas pueden tener un máximo de 5 instrucciones (observe que 3a y 3b se excluyen mutuamente):

|Instrucción|Código de operación supuestamente presente si:|Tamaño|Código de operación|Códigos de desenredado|
|-----------------|-----------------------------------|----------|------------|------------------|
|1|*H*== 1|16|`push {r0-r3}`|04|
|2|*C*== 1 o *L*== 1 o *R*== 0 o PF == 1|16/32|`push {registers}`|80-BF/D0-DF/EC-ED|
|3a|*C*== 1 y (*L*== 0 y *R*== 1 y PF == 0)|16|`mov r11,sp`|C0-CF/FB|
|3b|*C*== 1 y (*L*== 1 o *R*== 0 o PF == 1)|32|`add r11,sp,#xx`|FC|
|4|*R*== 1 y *Reg* ! = 7|32|`vpush {d8-dE}`|E0-E7|
|5|*Ajuste de pila* ! = 0 y PF == 0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|

Instrucción 1 siempre está presente si el *H* bit se establece en 1.

Para configurar el encadenamiento de marcos, la instrucción 3a o 3b está presente si el *C* bit está establecido. Es un `mov` de 16 bits si no se insertan más registros que r11 y LR; de lo contrario, es un `add` de 32 bits.

Si se especifica un ajuste de no plegamiento, la instrucción 5 será el ajuste de pila explícito.

Las instrucciones 2 y 4 se establecen en función de si se necesita una inserción. Esta tabla resumen los registros se guardan según el *C*, *L*, *R*, y *PF* campos. En todos los casos, *N* es igual a *Reg* + 4, *E* es igual a *Reg* + 8, y *S* es igual a (~*Ajustar la pila*) y 3.

|C|L|R|PF|Registros de enteros insertados|Registros de VFP insertados|
|-------|-------|-------|--------|------------------------------|--------------------------|
|0|0|0|0|R4-r*N*|ninguna|
|0|0|0|1|r*S*- r*N*|ninguna|
|0|0|1|0|ninguna|D8-d*E*|
|0|0|1|1|r*S*-r3|D8-d*E*|
|0|1|0|0|R4-r*N*, LR|ninguna|
|0|1|0|1|r*S*- r*N*, LR|ninguna|
|0|1|1|0|LR|D8-d*E*|
|0|1|1|1|r*S*-r3, LR|D8-d*E*|
|1|0|0|0|R4-r*N*, r11|ninguna|
|1|0|0|1|r*S*- r*N*, r11|ninguna|
|1|0|1|0|r11|D8-d*E*|
|1|0|1|1|r*S*-r3, r11|D8-d*E*|
|1|1|0|0|R4-r*N*, r11, LR|ninguna|
|1|1|0|1|r*S*- r*N*, r11, LR|ninguna|
|1|1|1|0|r11, LR|D8-d*E*|
|1|1|1|1|r*S*-r3, r11, LR|D8-d*E*|

Los epílogos de las funciones canónicas siguen un formato similar, pero a la inversa y con algunas opciones más. El epílogo puede tener una longitud de hasta 5 instrucciones, y su formato se define estrictamente por el formato del prólogo.

|Instrucción|Código de operación supuestamente presente si:|Tamaño|Código de operación|
|-----------------|-----------------------------------|----------|------------|
|6|*Ajuste de pila*! = 0 y *EF*== 0|16/32|`add   sp,sp,#xx`|
|7|*R*== 1 y *Reg*! = 7|32|`vpop  {d8-dE}`|
|8|*C*== 1 o (*L*== 1 y *H*== 0) o *R*== 0 o *EF*== 1|16/32|`pop   {registers}`|
|9a|*H*== 1 y *L*== 0|16|`add   sp,sp,#0x10`|
|9b|*H*== 1 y *L*== 1|32|`ldr   pc,[sp],#0x14`|
|10a|*RET*== 1|16|`bx    reg`|
|10b|*RET*== 2|32|`b     address`|

Si se especifica un ajuste de no plegamiento, la instrucción 6 será el ajuste de pila explícito. Dado que *PF* es independiente de *EF*, es posible que la instrucción 5 presente sin la instrucción 6, o viceversa.

Instrucciones 7 y 8 usan la misma lógica que el prólogo para determinar qué registros se restauran de la pila, pero con estos dos cambios: primero, *EF* se utiliza en lugar de *PF*; el segundo, si *Ret*  = 0, LR se reemplaza por PC en la lista de registros y el epílogo finaliza inmediatamente.

Si *H* se establece, a continuación, la instrucción 9a o 9b está presente. Instrucción 9a se usa cuando *L* es 0 para indicar que LR no está en la pila. En este caso, la pila se ajusta manualmente y *Ret* debe ser 1 o 2 para especificar una devolución explícita. Instrucción 9b se usa cuando *L* es 1, para señalar un final temprano del epílogo y para devolver y ajustar la pila al mismo tiempo.

Si el epílogo no ha finalizado aún, a continuación, cualquier instrucción 10a o 10b está presente, para indicar una bifurcación de 16 bits o 32 bits, según el valor de *Ret*.

### <a name="xdata-records"></a>Registros .xdata

Cuando el formato de desenredado empaquetado no basta para describir el desenredado de una función, se debe crear un registro .xdata de longitud variable. La dirección de este registro se almacena en la segunda palabra del registro .pdata. El formato de .xdata es un conjunto de palabras empaquetado y de longitud variable que consta de cuatro secciones:

1. Un encabezado de 1 o 2 palabras que indica el tamaño general de la estructura de .xdata y que proporciona datos de función fundamentales. La segunda palabra solo está presente si el *epílogo recuento* y *código palabras* campos se establecen en 0. Los campos aparecen detallados en esta tabla:

   |Palabra|Bits|Finalidad|
   |----------|----------|-------------|
   |0|0-17|*Función longitud* es un campo de 18 bits que indica la longitud total de la función en bytes, dividido por 2. Si una función supera los 512 KB, se deberán usar varios registros .pdata y .xdata para describir la función. Para obtener información detallada, vea la sección Funciones grandes en este documento.|
   |0|18-19|*Vers* es un campo de 2 bits que describe la versión de los xdata restantes. Actualmente solo está definida la versión 0; los valores 1-3 están reservados.|
   |0|20|*X* es un campo de 1 bit que indica la presencia (1) o ausencia (0) de datos de excepción.|
   |0|21|*E* es un campo de 1 bit que indica que la información que describe un único epílogo está empaquetada en el encabezado (1) en lugar de requerir ámbito adicional palabras posteriores (0).|
   |0|22|*F* es un campo de 1 bit que indica que este registro describe un fragmento de función (1) o una función completa (0). Un fragmento implica que no hay prólogo y que, por lo tanto, todo el procesamiento de prólogo se debe pasar por alto.|
   |0|23-27|*Recuento de epílogo* es un campo de 5 bits que tiene dos significados posibles, dependiendo del estado de la *E* bits:<br /><br /> -If *E* es 0, este campo es un recuento del número total de ámbitos de excepción que se describe en la sección 3. Si existen más de 31 ámbitos en la función y, a continuación, este campo y el *código palabras* campo debe establecerse ambas como 0 para indicar que se necesita una palabra de extensión.<br />-If *E* es 1, este campo especifica el índice del primer código de desenredado que describe el único epílogo.|
   |0|28-31|*Código palabras* es un campo de 4 bits que especifica el número de palabras de 32 bits necesario para contener todos los códigos de desenredado en la sección 4. Si se requieren más de 63 bytes de código de desenredado, este campo de más de 15 palabras y el *epílogo recuento* campo debe establecerse ambas como 0 para indicar que se necesita una palabra de extensión.|
   |1|0-15|*Cuenta de epílogo extendida* es un campo de 16 bits que proporciona más espacio para codificar un número inusualmente grande de epílogos. La palabra de extensión que contiene este campo solo está presente si el *epílogo recuento* y *código palabras* campos en la primera palabra del encabezado se establecen en 0.|
   |1|16-23|*Extended código palabras* es un campo de 8 bits que proporciona más espacio para codificar un número inusualmente grande de palabras de código de desenredado. La palabra de extensión que contiene este campo solo está presente si el *epílogo recuento* y *código palabras* campos en la primera palabra del encabezado se establecen en 0.|
   |1|24-31|Reservada|

1. Después de los datos de excepción (si la *E* bit en el encabezado se establece en 0) es una lista de información sobre los ámbitos de epílogo, que se empaquetan una a una palabra y se almacenan en orden creciente de desplazamiento inicial. Cada ámbito contiene estos campos:

   |Bits|Finalidad|
   |----------|-------------|
   |0-17|*Desplazamiento de inicio del epílogo* es un campo de 18 bits que describe el desplazamiento del epílogo, en bytes dividida entre 2, en relación con el inicio de la función.|
   |18-19|*Res* es un campo de 2 bits reservado para una futura expansión. Su valor debe ser 0.|
   |20-23|*Condición* es un campo de 4 bits que aporta la condición bajo la que se ejecuta el epílogo. En el caso de los epílogos incondicionales, se debe establecer en 0xE, lo que indica "siempre". (Un epílogo debe ser completamente condicional o completamente incondicional y, en el modo Thumb-2, el epílogo comienza por la primera instrucción tras el código de operación de IT).|
   |24-31|*Índice inicial de epílogo* es un campo de 8 bits que indica el índice de bytes del primer código de desenredado que describe este epílogo.|

1. Tras la lista de ámbitos de epílogo viene una matriz que contiene códigos de desenredado, que se detallan en profundidad en la sección Códigos de desenredado de este artículo. Esta matriz se rellena al final del límite de palabra completa más cercano. Los bytes se almacenan en orden little-endian, por lo que se pueden recuperar directamente en modo little-endian.

1. Si el *X* campo en el encabezado es 1, los bytes de código de desenredado van seguidos por la información del controlador de excepción. Esto se compone de uno *RVA del controlador de excepción* que contiene la dirección del controlador de excepciones, seguida inmediatamente de la cantidad (de longitud variable) de datos requeridos por el controlador de excepciones.

El registro .xdata está diseñado de forma que se pueden recuperar los primeros 8 bytes y calcular el tamaño completo del registro, sin incluir la longitud de los datos de tamaño variable que le siguen. En el siguiente fragmento de código se calcula el tamaño del registro:

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogueScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 23) != 0) {
        Size = 4;
        EpilogueScopes = (Xdata[0] >> 23) & 0x1f;
        UnwindWords = (Xdata[0] >> 28) & 0x0f;
    } else {
        Size = 8;
        EpilogueScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    if (!(Xdata[0] & (1 << 21))) {
        Size += 4 * EpilogueScopes;
    }
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;
    }
    return Size;
}
```

A pesar de que el prólogo y cada epílogo tienen un índice en los códigos de desenredado, comparten la tabla. No es inusual que todos compartan los mismos códigos de desenredado. Recomendamos a los autores de compiladores que optimicen esto, dado que el índice más grande que se puede especificar es de 255, lo cual constituye un límite para el número total de códigos de desenredado posibles de una función en particular.

### <a name="unwind-codes"></a>Códigos de desenredado

La matriz de códigos de desenredado es un conjunto de secuencias de instrucciones que describen exactamente cómo deshacer los efectos del prólogo en el orden en el que las operaciones deben realizarse. Los códigos de desenredado son un mini conjunto de instrucciones codificado como una cadena de bytes. Cuando la ejecución finaliza, la dirección de devolución a la función que llama se encuentra en el registro de LR, y todos los registros no volátiles se restauran a los valores que tenían establecidos en el momento en que se llamó a la función.

Si existiera la certeza de que solo pueden surgir excepciones dentro de un cuerpo de función (nunca en un prólogo o en un epílogo), únicamente sería necesaria una secuencia de desenredado. Sin embargo, el modelo de desenredado de Windows requiere la posibilidad de desenredar desde un prólogo o epílogo parcialmente ejecutado. A fin de dar cabida a este requisito, los códigos de desenredado se han diseñado meticulosamente de forma que tienen una asignación unívoca y no ambigua para cada código de operación relevante en el prólogo y el epílogo. Esto implica lo siguiente:

- Se puede calcular la longitud del prólogo y el epílogo a partir del recuento de códigos de desenredado. Esto es posible aun cuando existan instrucciones de Thumb-2 de longitud variable, ya que hay asignaciones diferentes para los códigos de operación de 16 y 32 bits.

- El recuento de instrucciones tras el inicio de un ámbito de epílogo permite omitir el número equivalente de códigos de desenredado y ejecutar el resto de una secuencia para completar el desenredado parcialmente ejecutado que el epílogo estaba llevando a cabo.

- El recuento de instrucciones antes del término del prólogo permite omitir el número equivalente de códigos de desenredado y ejecutar el resto de una secuencia para deshacer solo aquellas partes del prólogo cuya ejecución está completa.

En la siguiente tabla se muestra la asignación de códigos de desenredado a códigos de operación. Los códigos más comunes son de únicamente un byte, mientras que los menos habituales requieren dos, tres y hasta cuatro bytes. Cada código se almacena desde el byte más relevante al menos relevante. La estructura de códigos de desenredado difiere de la codificación descrita en la EABI de ARM, en el sentido de que estos códigos de desenredado están diseñados para tener una asignación unívoca con los códigos de operación en el prólogo y el epílogo y, así, permitir el desenredado de prólogos y epílogos ejecutados parcialmente.

|Byte 1|Byte 2|Byte 3|Byte 4|Tamaño de operación|Explicación|
|------------|------------|------------|------------|------------|-----------------|
|00-7F||||16|`add   sp,sp,#X`<br /><br /> donde X es (código y 0x7F) \* 4|
|80-BF|00-FF|||32|`pop   {r0-r12, lr}`<br /><br /> donde LR se extrae si Código y 0x2000 y r0-r12 se extraen si el bit correspondiente está establecido en Código y 0x1FFF|
|C0-CF||||16|`mov   sp,rX`<br /><br /> donde X es Código y 0x0F|
|D0-D7||||16|`pop   {r4-rX,lr}`<br /><br /> donde X es (Código y 0x03) + 4 y LR se extrae si Código y 0x04|
|D8-DF||||32|`pop   {r4-rX,lr}`<br /><br /> donde X es (Código y 0x03) + 8 y LR se extrae si Código y 0x04|
|E0-E7||||32|`vpop  {d8-dX}`<br /><br /> donde X es (Código y 0x07) + 8|
|E8-EB|00-FF|||32|`addw  sp,sp,#X`<br /><br /> donde X es (código y 0x03FF) \* 4|
|EC-ED|00-FF|||16|`pop   {r0-r7,lr}`<br /><br /> donde LR se extrae si Código y 0x0100 y r0-r7 se extraen si el bit correspondiente está establecido en Código y 0x00FF|
|EE|00-0F|||16|Específico de Microsoft|
|EE|10-FF|||16|Disponible|
|EF|00-0F|||32|`ldr   lr,[sp],#X`<br /><br /> donde X es (código y 0x000F) \* 4|
|EF|10-FF|||32|Disponible|
|F0-F4||||-|Disponible|
|F5|00-FF|||32|`vpop  {dS-dE}`<br /><br /> donde S es (Código y 0x00F0) >> 4 y E es Código y 0x000F|
|F6|00-FF|||32|`vpop  {dS-dE}`<br /><br /> donde S es ([Código y 0x00F0] >> 4) + 16 y E es (Código y 0x000F) + 16|
|F7|00-FF|00-FF||16|`add   sp,sp,#X`<br /><br /> donde X es (código y 0x00FFFF) \* 4|
|F8|00-FF|00-FF|00-FF|16|`add   sp,sp,#X`<br /><br /> donde X es (código y 0x00FFFFFF) \* 4|
|F9|00-FF|00-FF||32|`add   sp,sp,#X`<br /><br /> donde X es (código y 0x00FFFF) \* 4|
|FA|00-FF|00-FF|00-FF|32|`add   sp,sp,#X`<br /><br /> donde X es (código y 0x00FFFFFF) \* 4|
|FB||||16|nop (16 bits)|
|FC||||32|nop (32 bits)|
|FD||||16|fin + nop de 16 bits en el epílogo|
|FE||||32|fin + nop de 32 bits en el epílogo|
|FF||||-|end|

Esto muestra el intervalo de valores hexadecimales para cada byte en un código de desenredado *código*, junto con el tamaño del código de operación *Opsize* y la interpretación de las instrucciones originales correspondiente. Las celdas vacías señalan códigos de desenredado más breves. En las instrucciones en las que hay valores grandes que ocupan múltiples bytes, los bits más relevantes son los que están almacenados en primer lugar. El *Opsize* campo muestra el tamaño del código de operación implícito asociado con cada operación de Thumb-2. Las entradas duplicadas más que evidentes de la tabla con distintas codificaciones sirven para distinguir los diferentes tamaños de código de operación.

Los códigos de desenredado están diseñados de forma que el primer byte del código informa tanto del tamaño total en bytes del código como del tamaño del código de operación correspondiente en la secuencia de instrucciones. Para calcular el tamaño del prólogo o el epílogo, recorra los códigos de desenredado de principio a fin de la secuencia y use una tabla de búsqueda o método similar para averiguar la longitud del código de operación correspondiente.

Los códigos de desenredado 0xFD y 0xFE equivalen al código de fin regular 0xFF, pero cuentan con un código de operación nop (sin operación) extra para el epílogo, sea de 16 o de 32 bits. En el caso de los prólogos, los códigos 0xFD, 0xFE y 0xFF son totalmente equivalentes. Esto tiene en cuenta las finalizaciones de epílogo habituales `bx lr` o `b <tailcall-target>`, que carecen de una instrucción de prólogo equivalente, lo que aumenta las posibilidades de que el prólogo y los epílogos puedan compartir las secuencias de desenredado.

En muchas ocasiones, debería poder utilizarse el mismo conjunto de códigos de desenredado en el prólogo y en todos los epílogos. Sin embargo, tendríamos que disponer de varias secuencias de código de desenredado con diferente orden y comportamiento para poder controlar el desenredado de los prólogos y epílogos parcialmente ejecutados. Este es el motivo por el que cada epílogo tiene su propio índice en la matriz de desenredado con el que se señala dónde ha de empezar la ejecución.

### <a name="unwinding-partial-prologues-and-epilogues"></a>Desenredado de prólogos y epílogos parciales

La situación de desenredado más habitual tiene lugar cuando se produce una excepción en el cuerpo de la función, que no tiene nada que ver con el prólogo y ninguno de los epílogos. En tal caso, el responsable del desenredado ejecuta los códigos de la matriz de desenredado, empezando por el índice 0 y continuando hasta que se detecta un fin de código de operación.

Si se produce una excepción mientras un prólogo o un epílogo se está ejecutando, el marco de la pila solo se construirá de forma parcial, por lo que el responsable del desenredado deberá averiguar exactamente qué se ha realizado hasta el momento para poder deshacerlo correctamente.

Supongamos, por ejemplo, la siguiente secuencia de prólogo y epílogo:

```asm
0000:   push  {r0-r3}         ; 0x04
0002:   push  {r4-r9, lr}     ; 0xdd
0006:   mov   r7, sp          ; 0xc7
...
0140:   mov   sp, r7          ; 0xc7
0142:   pop   {r4-r9, lr}     ; 0xdd
0146:   add   sp, sp, #16     ; 0x04
0148:   bx    lr
```

Junto a cada código de operación está el código de desenredado pertinente, que describe la operación. La secuencia de códigos de desenredado del prólogo es una imagen reflejada de los códigos de desenredado del epílogo, sin contar la instrucción final. Esto es bastante habitual y constituye el motivo por el cual siempre se da por hecho que los códigos de desenredado del prólogo se almacenan en orden inverso al orden de ejecución del epílogo. Esto nos proporciona un conjunto común de códigos de desenredado:

```asm
0xc7, 0xdd, 0x04, 0xfd
```

El código 0xFD es un código especial para la finalización de la secuencia que quiere decir que el epílogo es una instrucción de 16 bits más larga que el prólogo. Esto permite que se puedan compartir un mayor número de códigos de desenredado.

En este ejemplo, si tiene lugar una excepción mientras el cuerpo de la función entre el prólogo y el epílogo se está ejecutando, el desenredado se inicia con el epílogo, con un desplazamiento 0 en el código del epílogo. Esto corresponde al desplazamiento 0x140 del ejemplo. El responsable del desenredado ejecuta la secuencia de desenredado completa, porque no se ha efectuado ninguna limpieza. Si, en lugar de esto, la excepción se produjera en una instrucción posterior al inicio del código del epílogo, el responsable del desenredado podrá realizar el desenredado correctamente omitiendo el primer código de desenredado. Con una asignación unívoca entre códigos de operación y códigos de desenredado, si desenredamos desde la instrucción *n* en el epílogo, el responsable del desenredado debería omitir los primeros *n* códigos de desenredado.

Esta misma lógica es perfectamente válida, pero a la inversa, para el prólogo. Si desenredamos desde el desplazamiento 0 del prólogo, no hay que ejecutar nada. Si desenredamos desde una instrucción, la secuencia de desenredado debería iniciar un código de desenredado del final, ya que los códigos de desenredado del prólogo se almacenan en orden inverso. Por lo general, si desenredamos desde la instrucción *n* en el prólogo, desenredado debería empezar a ejecutarse en *n* códigos desde el final de la lista de códigos de desenredado.

Los códigos de desenredado del prólogo y los epílogos no siempre coinciden plenamente. En tal caso, la matriz de códigos de desenredado puede contener varias secuencias de códigos. Emplee la siguiente lógica para averiguar el desplazamiento por el que empezar a procesar códigos:

1. Si desenreda desde el cuerpo de la función, empiece a ejecutar códigos de desenredado en el índice 0 y continúe hasta llegar a un fin de código de operación.

2. Si desenreda desde un epílogo, utilice el índice de inicio específico de dicho epílogo, suministrado por el ámbito del epílogo. Calcule el número de bytes del PC desde el inicio del epílogo. Avance por los códigos de desenredado hasta haber pasado por todas las instrucciones que ya se han ejecutado. Ejecute la secuencia de desenredado a partir de ese punto.

3. Si desenreda desde el prólogo, comience desde el índice 0 de los códigos de desenredado. Calcule la longitud del código del prólogo desde la secuencia y, luego, calcule el número de bytes del PC desde la finalización del prólogo. Avance por los códigos de desenredado hasta haber pasado por todas las instrucciones que no se han ejecutado. Ejecute la secuencia de desenredado a partir de ese punto.

Los códigos de desenredado del prólogo siempre deben ser los primeros de la matriz, puesto que también son los códigos que se usan para desenredar en el caso general de desenredado desde el cuerpo de la función. Todas las secuencias de código específicas de los epílogos deben ir inmediatamente después de la secuencia de código del prólogo.

### <a name="function-fragments"></a>Fragmentos de función

A fin de optimizar el código, resulta bastante útil dividir una función en partes no contiguas. Cuando esto sucede, cada fragmento de la función necesita tener su propio registro .pdata (y, probablemente, también un registro .xdata).

Suponiendo que el prólogo de la función se encuentra al inicio de la función y que no se puede dividir, existen cuatro casos de fragmento de función:

- Solo prólogo; todos los epílogos están en otros fragmentos.

- Prólogo y uno o más epílogos; el resto de epílogos está en otros fragmentos.

- Sin prólogo ni epílogos; el prólogo y uno o más epílogos están en otros fragmentos.

- Solo epílogos; el prólogo y, posiblemente, otros epílogos están en otros fragmentos.

En el primer caso, solo hay que describir el prólogo. Esto puede hacerse en formato compacto .pdata, describiendo el prólogo normalmente y especifique un *Ret* valor 3 para no indicar ningún epílogo. En el formato .xdata completo, esto se lleva a cabo proporcionando los códigos de desenredado del prólogo en el índice 0 (como habitualmente) y especificando 0 como recuento de epílogos.

El segundo caso es, sencillamente, el de una función normal. Si solo hay un epílogo en el fragmento y se encuentra al final de este, se puede usar un registro .pdata compacto. Si no, se deberá utilizar un registro .xdata completo. Recuerde que los desplazamientos especificados como inicio de epílogo lo son con respecto al inicio del fragmento, no al inicio original de la función.

Los casos tercero y cuarto son variantes del primero y el segundo respectivamente, solo que no contienen un prólogo. En estas situaciones, se da por hecho que existe código antes del inicio del epílogo y se considera como parte del cuerpo de la función, lo que normalmente podría desenredarse deshaciendo los efectos del prólogo. Por lo tanto, estos casos deben estar codificados con un seudoprólogo, en el que se explica cómo desenredar desde el cuerpo, si bien tratado como con una longitud 0 al decidir si hay que realizar un desenredo parcial al inicio del fragmento. Otra opción consiste en describir este seudoprólogo mediante los mismos códigos de desenredado que el epílogo, ya que en teoría realizan las mismas operaciones.

En los casos terceros y cuarto, la presencia de un seudoprólogo se especifica ya sea estableciendo la *marca* campo del registro .pdata compacto en 2, o estableciendo la *F* marca en el encabezado de .xdata en 1. En cualquier caso, se pasa por alto la comprobación de un desenredado de prólogo parcial y todos los desenredados que no sean de epílogo se considerarán como completos.

#### <a name="large-functions"></a>Funciones grandes

Los fragmentos se pueden usar para describir funciones con un tamaño superior al límite de 512 KB impuesto por los campos de bits en el encabezado de .xdata. Para describir una función muy grande, basta con dividirla en fragmentos de un tamaño inferior a 512 KB. Cada fragmento se debe ajustar de forma que no divida un epílogo en varias partes.

Solo el primer fragmento de la función contiene un prólogo; todos los demás están marcados como carentes de prólogo. Según cuál sea el número de epílogos, cada fragmento puede contener cero o más epílogos. Recuerde que cada ámbito de epílogo en un fragmento especifica su desplazamiento de inicio con respecto al inicio del fragmento, no al inicio original de la función.

Si un fragmento no tiene ni prólogo ni epílogo, seguirá necesitando su propio registro .pdata (y, probablemente, también un registro .xdata) para describir cómo llevar a cabo el desenredo desde el cuerpo de la función.

#### <a name="shrink-wrapping"></a>Reducción hasta ajustar

Es un caso especial más complejo de fragmentos de función *reducción*, guarda una técnica para aplazar desde el principio de la función que más adelante en la función, para optimizar los casos sencillos que no es necesario guardar registros. Se podría describir como una región externa que asigna espacio de la pila, pero que guarda un conjunto mínimo de registros, y una región interna que guarda y restaura más registros.

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatiles
    sub    sp, sp, #0x100    ; A: allocate all stack space up front
    ...                      ; A:
    add    r0, sp, #0xE4     ; A: prepare to do the inner save
    stm    r0, {r5-r11}      ; A: save remaining non-volatiles
    ...                      ; B:
    add    r0, sp, #0xE4     ; B: prepare to do the inner restore
    ldm    r0, {r5-r11}      ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C:
```

Por lo general, se espera que las funciones reducidas hasta ajustarse tengan espacio previamente asignado para el almacenamiento de registros extra en el prólogo regular para, luego, guardarlos mediante `str` o `stm` en lugar de `push`. Esto hace que toda la manipulación de puntero de pila tenga lugar en el prólogo original de la función.

La función reducida hasta ajustarse de ejemplo se debe dividir en tres regiones, marcadas como A, B y C en los comentarios. La primera región, A, abarca el inicio de la función y hasta el final de los almacenamientos no volátiles extra. Se debe crear un registro .pdata o .xdata para describir que este fragmento tiene un prólogo y ningún epílogo.

La región central, B, tiene su propio registro .pdata o .xdata que describe que un fragmento no tiene ni prólogo ni epílogo. Sin embargo, debe seguir habiendo códigos de desenredado para esta región, ya que se considera un cuerpo de función. Los códigos deben describir un prólogo compuesto que representa tanto los registros originales guardados en el prólogo de la región A como los registros extra guardados antes de entrar en la región B, como si hubieran sido generados por una sola secuencia de operaciones.

El almacenamiento de registros de la región B no se puede considerar como un "prólogo interno", ya que el prólogo compuesto descrito para la región B debe detallar tanto el prólogo de la región A como los registros adicionales guardados. Si se especificara que el fragmento B tiene un prólogo, los códigos de desenredado también darían a entender el tamaño de dicho prólogo, y no existe manera de describir el prólogo compuesto de manera que se asigne de modo unívoco con los códigos de operación que solo guardan los registros adicionales.

El almacenamiento de registros adicionales se debe considerar como parte de la región A porque, hasta que no se han completado, el prólogo compuesto no describe el estado de la pila con exactitud.

La última región, C, tiene su propio registro .pdata o .xdata que describe que un fragmento no tiene prólogo, pero sí epílogo.

Existe otro método que puede funcionar si la manipulación de pila realizada antes de entrar en la región B se puede reducir a una instrucción:

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatile registers
    sub    sp, sp, #0xE0     ; A: allocate minimal stack space up front
    ...                      ; A:
    push   {r4-r9}           ; A: save remaining non-volatiles
    ...                      ; B:
    pop    {r4-r9}           ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C: restore non-volatile registers
```

Aquí, la clave consiste en que, en cada límite de instrucción, la pila es totalmente coherente con los códigos de desenredado de la región. Si se produce un desenredado antes de la inserción interior en este ejemplo, se considerará como parte de la región A y, como tal, solo se desenredará el prólogo de la región A. Si el desenredado se produce después de la inserción interior, se considera parte de la región B, que no tiene prólogo, pero tiene códigos de desenredado que describen la inserción interior como en el prólogo original de la región A. esta misma lógica se mantiene durante la extracción interior.

### <a name="encoding-optimizations"></a>Codificación de optimizaciones

Dada la riqueza de los códigos de desenredado y la posibilidad de utilizar los formatos de datos compacto y expandido, existen numerosas oportunidades de optimizar la codificación para reducir aún más el espacio. Si se hace un uso riguroso de estas técnicas, la sobrecarga de red motivada por la descripción de funciones y fragmentos mediante códigos de desenredado puede ser realmente mínima.

Lo más importante es tener cuidado de no confundir los límites de prólogo/epílogo a la hora de realizar operaciones de desenredado con los límites lógicos de prólogo/epílogo desde el punto de vista del compilador. Los límites de desenredado se pueden reducir y ser más estrictos de cara a mejorar la eficiencia. Así, por ejemplo, un prólogo puede contener código tras la configuración de la pila destinado a realizar más comprobaciones, pero, una vez que se completen todas las manipulaciones de la pila, ya no será necesario codificar más operaciones, por lo que todo el código que haya tras esto se podrá eliminar del prólogo de desenredado.

Esta regla es igualmente válida para la longitud de la función. Si hay datos (un grupo de literales, por ejemplo) tras un epílogo en una función, no deben incluirse como parte de la longitud de la función. Al reducir la función a exclusivamente el código que forma parte de la función, es bastante más probable que el epílogo esté justamente al final y se puede usar un registro .pdata compacto.

En un prólogo, una vez que el puntero de pila se ha guardado en otro registro, normalmente no hay necesidad de registrar más códigos de operación. Para desenredar la función, lo primero que se hace es recuperar el SP del registro guardado, ya que así las operaciones posteriores no tendrán impacto alguno en el desenredado.

Los epílogos con una sola instrucción no tienen que codificarse en absoluto, ni como ámbitos ni como códigos de desenredado. Si se produce un desenredado antes de que esa instrucción se ejecute, supuestamente lo hará desde el cuerpo de la función, con lo que bastará con ejecutar los códigos de desenredado del prólogo. Si el desenredado se produce después de que esa única instrucción se ejecute, lo hará por definición en otra región.

No es necesario codificar la primera instrucción del epílogo, por el mismo motivo señalado anteriormente epílogos con varias instrucciones: si el desenredado de lleva a cabo antes de esa instrucción se ejecute, un desenredado de prólogo completo será suficiente. Si el desenredado se produce tras la instrucción, solo habrá que tener en cuenta las operaciones subsiguientes.

La reutilización de códigos de desenredado debe ser rigurosa. El índice especificado por cada ámbito de epílogo señala a un punto de inicio arbitrario de la matriz de códigos de desenredado. No tiene que apuntar al inicio de una secuencia anterior, puede señalar a un punto intermedio. El mejor método en este sentido consiste en generar la secuencia de código deseada y, luego, buscar una coincidencia exacta de byte en el grupo de secuencias ya codificado y utilizar cualquier coincidencia exacta como punto de partida de reutilización.

Si, tras omitir los epílogos con una sola instrucción, no hay más epílogos, considere la posibilidad de usar un formato de .pdata compacto; es mucho más probable ante la ausencia de un epílogo.

## <a name="examples"></a>Ejemplos

En los siguientes ejemplos, la base de imagen está a 0x00400000.

### <a name="example-1-leaf-function-no-locals"></a>Ejemplo 1: Función de hoja, sin asignaciones locales

```asm
Prologue:
  004535F8: B430      push        {r4-r5}
Epilogue:
  00453656: BC30      pop         {r4-r5}
  00453658: 4770      bx          lr
```

.pdata (fijo, 2 palabras):

- Palabra 0

   - *Inicio de la función RVA* = 0x000535F8 (= 0x004535F8-0 x 00400000)

- Palabra 1

   - *Marca* = 1, que indica los formatos de prólogo y epílogo canónicos

   - *Función longitud* = 0 x 31 (= 0 x 62/2)

   - *RET* = 1, indica que una bifurcación de 16 bits de valor devuelta

   - *H* = 0, indica que los parámetros no se albergaron

   - *R*= 0 y *Reg* = 1, indica inserción/extracción de r4-r5

   - *L* = 0, indica que no hay LR guardar ni restaurar

   - *C* = 0, indica que no hay encadenamiento de marcos

   - *Ajustar la pila* = 0, indica que ningún ajuste de pila

### <a name="example-2-nested-function-with-local-allocation"></a>Ejemplo 2: La función anidada con asignación Local

```asm
Prologue:
  004533AC: B5F0      push        {r4-r7, lr}
  004533AE: B083      sub         sp, sp, #0xC
Epilogue:
  00453412: B003      add         sp, sp, #0xC
  00453414: BDF0      pop         {r4-r7, pc}
```

.pdata (fijo, 2 palabras):

- Palabra 0

   - *Inicio de la función RVA* = 0x000533AC (= 0x004533AC-0 x 00400000)

- Palabra 1

   - *Marca* = 1, que indica los formatos de prólogo y epílogo canónicos

   - *Función longitud* = 0 x 35 (= 0x6A/2)

   - *RET* = 0, indica un retorno extracción {pc}

   - *H* = 0, indica que los parámetros no se albergaron

   - *R*= 0 y *Reg* = 3, indica inserción/extracción de r4-r7

   - *L* = 1, indica que el LR se guardó/restauró

   - *C* = 0, indica que no hay encadenamiento de marcos

   - *Ajuste de pila* = 3 (= 0x0C/4)

### <a name="example-3-nested-variadic-function"></a>Ejemplo 3: Función Variádica anidada

```asm
Prologue:
  00453988: B40F      push        {r0-r3}
  0045398A: B570      push        {r4-r6, lr}
Epilogue:
  004539D4: E8BD 4070 pop         {r4-r6}
  004539D8: F85D FB14 ldr         pc, [sp], #0x14
```

.pdata (fijo, 2 palabras):

- Palabra 0

   - *Inicio de la función RVA* = 0x00053988 (= 0x00453988-0 x 00400000)

- Palabra 1

   - *Marca* = 1, que indica los formatos de prólogo y epílogo canónicos

   - *Función longitud* = 0x2A (= 0 x 54/2)

   - *RET* = 0, indica una extracción {pc}-return de estilo (en este caso un pc ldr, [sp], # 0 x 14 devolver)

   - *H* = 1, que indica los parámetros se albergaron

   - *R*= 0 y *Reg* = 2, indica inserción/extracción de r4-r6

   - *L* = 1, indica que el LR se guardó/restauró

   - *C* = 0, indica que no hay encadenamiento de marcos

   - *Ajustar la pila* = 0, indica que ningún ajuste de pila

### <a name="example-4-function-with-multiple-epilogues"></a>Ejemplo 4: Función con varios epílogos

```asm
Prologue:
  004592F4: E92D 47F0 stmdb       sp!, {r4-r10, lr}
  004592F8: B086      sub         sp, sp, #0x18
Epilogues:
  00459316: B006      add         sp, sp, #0x18
  00459318: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  0045943E: B006      add         sp, sp, #0x18
  00459440: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  004595D4: B006      add         sp, sp, #0x18
  004595D6: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459606: B006      add         sp, sp, #0x18
  00459608: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459636: F028 FF0F bl          KeBugCheckEx     ; end of function
```

.pdata (fijo, 2 palabras):

- Palabra 0

   - *Inicio de la función RVA* = 0x000592F4 (= 0x004592F4-0 x 00400000)

- Palabra 1

   - *Marca* = 0, que indica que un registro .xdata (necesario debido a varios epílogos)

   - *dirección de .xdata* -0 x 00400000

.xdata (variable, 6 palabras):

- Palabra 0

   - *Función longitud* = 0x0001A3 (= 0x000346/2)

   - *Vers* = 0, indica que la primera versión de xdata

   - *X* = 0, indica que no hay datos de excepción

   - *E* = 0, indica una lista de ámbitos de epílogo

   - *F* = 0, indica una descripción de la función completa, prólogo incluido

   - *Recuento de epílogo* = 0 x 04, que indica los 4 ámbitos de epílogo total

   - *Código palabras* = 0 x 01, que indica una palabra de 32 bits de códigos de desenredado

- Palabras 1-4, que describen los 4 ámbitos de epílogo en las 4 ubicaciones. Cada ámbito tiene un conjunto común de códigos de desenredado compartido con el prólogo (en un desplazamiento de 0x00) y es incondicional, especifica la condición 0x0E (siempre).

- Códigos de desenredado, empezando por la palabra 5: (compartido entre el prólogo y epílogo)

   - 0 = 0 x 06 de código de desenredado: += sp (6 << 2)

   - 1 = 0xDE código de desenredado: pop {r4 a r10, lr}

   - Código de desenredado 2 = 0xFF: final

### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>Ejemplo 5: Función con pila dinámica y epílogo interior

```asm
Prologue:
  00485A20: B40F      push        {r0-r3}
  00485A22: E92D 41F0 stmdb       sp!, {r4-r8, lr}
  00485A26: 466E      mov         r6, sp
  00485A28: 0934      lsrs        r4, r6, #4
  00485A2A: 0124      lsls        r4, r4, #4
  00485A2C: 46A5      mov         sp, r4
  00485A2E: F2AD 2D90 subw        sp, sp, #0x290
Epilogue:
  00485BAC: 46B5      mov         sp, r6
  00485BAE: E8BD 41F0 ldm         sp!, {r4-r8, lr}
  00485BB2: B004      add         sp, sp, #0x10
  00485BB4: 4770      bx          lr
  ...
  00485E2A: F7FF BE7D b           #0x485B28    ; end of function
```

.pdata (fijo, 2 palabras):

- Palabra 0

   - *Inicio de la función RVA* = 0x00085A20 (= 0x00485A20-0 x 00400000)

- Palabra 1

   - *Marca* = 0, que indica que un registro .xdata (necesario debido a que hay varios epílogos)

   - *dirección de .xdata* -0 x 00400000

.xdata (variable, 3 palabras):

- Palabra 0

   - *Función longitud* = 0x0001A3 (= 0x000346/2)

   - *Vers* = 0, indica que la primera versión de xdata

   - *X* = 0, indica que no hay datos de excepción

   - *E* = 0, indica una lista de ámbitos de epílogo

   - *F* = 0, indica una descripción de la función completa, prólogo incluido

   - *Recuento de epílogo* = 0 x 001, que indica el ámbito de epílogo total 1

   - *Código palabras* = 0 x 01, que indica una palabra de 32 bits de códigos de desenredado

- Palabra 1: Ámbito de epílogo en el desplazamiento 0xC6 (= 0x18C/2), a partir de índice de código de desenredado 0 x 00, con una condición de 0x0E (siempre)

- Códigos de desenredado, empezando por la palabra 2: (compartido entre el prólogo y epílogo)

   - 0 = 0xC6 código de desenredado: sp = r6

   - 1 = 0xDC código de desenredado: pop {r4 r8, lr}

   - 2 = 0 x 04 de código de desenredado: += sp (4 << 2)

   - 3 = 0xFD código de desenredado: end, cuenta como instrucción de 16 bits para el epílogo

### <a name="example-6-function-with-exception-handler"></a>Ejemplo 6: Función con controlador de excepciones

```asm
Prologue:
  00488C1C: 0059 A7ED dc.w  0x0059A7ED
  00488C20: 005A 8ED0 dc.w  0x005A8ED0
FunctionStart:
  00488C24: B590      push        {r4, r7, lr}
  00488C26: B085      sub         sp, sp, #0x14
  00488C28: 466F      mov         r7, sp
Epilogue:
  00488C6C: 46BD      mov         sp, r7
  00488C6E: B005      add         sp, sp, #0x14
  00488C70: BD90      pop         {r4, r7, pc}
```

.pdata (fijo, 2 palabras):

- Palabra 0

   - *Inicio de la función RVA* = 0x00088C24 (= 0x00488C24-0 x 00400000)

- Palabra 1

   - *Marca* = 0, que indica que un registro .xdata (necesario debido a que hay varios epílogos)

   - *dirección de .xdata* -0 x 00400000

.xdata (variable, 5 palabras):

- Palabra 0

   - *Función longitud* = 0x000027 (= 0x00004E/2)

   - *Vers* = 0, indica que la primera versión de xdata

   - *X* = 1, que indica los datos de excepción está presentes

   - *E* = 1, indica que un solo epílogo

   - *F* = 0, indica una descripción de la función completa, prólogo incluido

   - *Recuento de epílogo* = 0 x 00, que indica los códigos de desenredado de epílogo comienzan en el desplazamiento 0 x 00

   - *Código palabras* = 0 x 02, que indica dos palabras de 32 bits de códigos de desenredado

- Códigos de desenredado, empezando por la palabra 1:

   - 0 = 0xC7 código de desenredado: sp = r7

   - 1 = 0 x 05 de código de desenredado: += sp (5 << (2).

   - 2 = 0xED/0 x 90 del código de desenredado: pop {r4, r7, lr}

   - Código de desenredado 4 = 0xFF: final

- Palabra 3 especifica un controlador de excepciones = 0x0019A7ED (= 0x0059A7ED - 0 x 00400000)

- Las palabras 4 en adelante son datos de excepción insertados

### <a name="example-7-funclet"></a>Ejemplo 7: Funclet

```asm
Function:
  00488C72: B500      push        {lr}
  00488C74: B081      sub         sp, sp, #4
  00488C76: 3F20      subs        r7, #0x20
  00488C78: F117 0308 adds        r3, r7, #8
  00488C7C: 1D3A      adds        r2, r7, #4
  00488C7E: 1C39      adds        r1, r7, #0
  00488C80: F7FF FFAC bl          target
  00488C84: B001      add         sp, sp, #4
  00488C86: BD00      pop         {pc}
```

.pdata (fijo, 2 palabras):

- Palabra 0

   - *Inicio de la función RVA* = 0x00088C72 (= 0x00488C72-0 x 00400000)

- Palabra 1

   - *Marca* = 1, que indica los formatos de prólogo y epílogo canónicos

   - *Función longitud* = 0x0B (= 0 x 16/2)

   - *RET* = 0, indica un retorno extracción {pc}

   - *H* = 0, indica que los parámetros no se albergaron

   - *R*= 0 y *Reg* = 7, que indica sin registros eran guardó/restauró

   - *L* = 1, indica que el LR se guardó/restauró

   - *C* = 0, indica que no hay encadenamiento de marcos

   - *Ajustar la pila* = 1, que indica un ajuste de pila de 1 × 4 bytes

## <a name="see-also"></a>Vea también

[Información general sobre las convenciones ABI de ARM](../build/overview-of-arm-abi-conventions.md)<br/>
[Problemas comunes de migración de ARM en Visual C++](../build/common-visual-cpp-arm-migration-issues.md)
