---
title: Error del compilador de recursos RW2002
ms.date: 11/04/2016
f1_keywords:
- RW2002
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
ms.openlocfilehash: 1726e6ce74dfd7b6b0c6e4b69771a826cdf07774
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230403"
---
# <a name="resource-compiler-error-rw2002"></a>Error del compilador de recursos RW2002

Error de análisis

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. **Tipo de acelerador necesario (ASCII o VIRTKEY)**

   El campo `type` de la instrucción **ACCELERATORS** debe contener el valor ASCII o VIRTKEY.

1. **Se esperaba BEGIN en la tabla de aceleradores**

   La palabra clave **BEGIN** debe aparecer inmediatamente después de la palabra clave **ACCELERATORS** .

1. **Se esperaba BEGIN en el cuadro de diálogo**

   La palabra clave **Begin** debe seguir inmediatamente a la palabra clave **Dialog** .

1. **Se esperaba BEGIN en el menú**

   La palabra clave **BEGIN** debe aparecer inmediatamente después de la palabra clave **MENU** .

1. **Se esperaba BEGIN en RCData**

   La palabra clave **BEGIN** debe aparecer inmediatamente después de la palabra clave **RCDATA** .

1. **Se esperaba la palabra clave BEGIN en la tabla de cadenas**

   La palabra clave **Begin** debe seguir inmediatamente a la palabra clave **stringtable** .

1. **No se pueden volver a usar constantes de cadena**

   Está utilizando el mismo valor dos veces en una instrucción **stringtable** . Asegúrese de que no está mezclando valores decimales y hexadecimales superpuestos. Cada identificador de una **stringtable** debe ser único. Para obtener la máxima eficacia, use constantes contiguas que se inician en un múltiplo de 16.

1. **Carácter de control fuera del intervalo [^ A-^ Z]**

   Un carácter de control en la instrucción **ACELERAtors** no es válido. El carácter que sigue al símbolo de intercalación ( **^** ) debe estar comprendido entre A y Z, ambos inclusive.

1. **No se permiten menús vacíos**

   Aparece una palabra clave **End** antes de que se defina algún elemento de menú en la instrucción de **menú** . El compilador de recursos no permite menús vacíos. Asegúrese de que no tiene Comillas abiertas en la instrucción de **menú** .

1. **Se esperaba END en el cuadro de diálogo**

   La palabra clave **End** debe aparecer al final de una instrucción **Dialog** . Asegúrese de que no quedan comillas abiertas de la instrucción anterior.

1. **Se esperaba END en el menú**

   La palabra clave **END** debe aparecer al final de una instrucción **MENU** . Asegúrese de que no tenga ningún signo de comillas abierto ni una pareja que no coincida de instrucciones **BEGIN** y **END** .

1. **Coma esperada en la tabla de aceleradores**

   El compilador de recursos requiere una coma entre los campos `event` idvalue *y* de la instrucción **ACCELERATORS** .

1. **Se esperaba un nombre de clase de control**

   El `class` campo de una instrucción de **control** en la instrucción **Dialog** debe ser uno de los siguientes tipos: BUTTON, COMBOBOX, EDIT, LISTBOX, SCROLLBAR, STATIC o definidos por el usuario. Asegúrese de que la clase está escrita correctamente.

1. **Se esperaba un nombre de fuente**

   El campo *typeface* de la opción FONT de la instrucción **DIALOG** debe ser una cadena de carácter ASCII entre comillas dobles. Este campo especifica el nombre de una fuente.

1. **Se esperaba un valor de identificador para MenuItem**

   La instrucción **MENU** debe contener un campo *menuID* que especifique el nombre o el número que identifica el recurso de menú.

1. **Se esperaba una cadena de menú**

   Cada una de las instrucciones **MENUITEM** y **POPUP** debe contener un campo *text* , que es una cadena entre comillas dobles que especifica el nombre del elemento de menú o menú de elemento emergente. Una instrucción **MenuItem separator** no requiere ninguna cadena entrecomillada.

1. **Valor de comando numérico esperado**

   El compilador de recursos esperaba un campo *idvalue* numérico en la instrucción **Accelerators** . Asegúrese de que ha usado una `#define` constante para especificar el valor y que la constante está escrita correctamente.

1. **Se esperaba una constante numérica en la tabla de cadenas**

   Una constante numérica, definida en una instrucción `#define` debe seguir inmediatamente a la palabra clave **BEGIN** en una instrucción **STRINGTABLE** .

1. **Se esperaba un tamaño de punto numérico**

   El campo *pointsize* de la opción FONT en la instrucción **DIALOG** debe ser un valor entero de tamaño de punto.

1. **Se esperaba una constante de cuadro de diálogo numérica**

   Una instrucción **Dialog** requiere valores enteros para los campos *x, y, ancho*y *alto* . Asegúrese de que estos valores se incluyen después de la palabra clave **Dialog** y que no son negativos.

1. **Se esperaba una cadena en STRINGTABLE**

   Se espera una cadena después de cada valor *stringid* en una instrucción **STRINGTABLE** .

1. **Comando de acelerador de constante o cadena esperado**

   El compilador de recursos no pudo determinar qué tipo de clave se va a configurar para el acelerador. El campo `event` de la instrucción **ACCELERATOS** podría no ser válido.

1. **Se espera un número para el identificador**

   Se espera un número para `id` el campo de una instrucción de control en la instrucción de **cuadro de diálogo** . Asegúrese de que tiene un número o `#define` una instrucción para el ID. de control.

1. **Se espera una cadena entrecomillada en una clase de cuadro de diálogo**

   El campo `class` de la opción CLASS en la instrucción **DIALOG** debe ser un entero o una cadena entre comillas dobles.

1. **Se espera una cadena entrecomillada en el título del cuadro de diálogo**

   El campo `captiontext` de la opción CAPTION de la instrucción **DIALOG** debe ser una cadena de caracteres ASCII entre comillas dobles.

1. **Archivo no encontrado: nombre de archivo**

   No se encontró el archivo especificado en la línea de comandos del compilador de recursos. Compruebe si el archivo se ha movido a otro directorio y si se ha escrito correctamente el nombre de archivo o ruta de acceso. Los archivos se buscan usando la variable de entorno **include** o la configuración de Visual Studio, si está disponible.

1. **Los nombres de fuente deben ser ordinales**

   El campo de *puntuación* de la instrucción Font debe ser un entero, no una cadena.

1. **Acelerador no válido**

   Un campo `event` en la instrucción **ACCELERATORS** no se reconoce o tenía más de dos caracteres de longitud.

1. **Tipo de acelerador no válido (ASCII o VIRTKEY)**

   El campo `type` de la instrucción **ACCELERATORS** debe contener el valor ASCII o VIRTKEY.

1. **Carácter de control no válido**

   Un carácter de control en la instrucción **ACELERAtors** no es válido. Un carácter de control válido se compone de una letra (solo) después de un símbolo de intercalación (^).

1. **Tipo de control no válido**

   Cada instrucción de control de una instrucción **Dialog** debe ser una de las siguientes: CHECKBOX, COMBOBOX, CONTROL, CTEXT, DEFPUSHBUTTON, EDITTEXT, GROUPBOX, ICON, LISTBOX, LTEXT, PUSHBUTTON, RADIOBUTTON, RTEXT, SCROLLBAR. Asegúrese de que estas instrucciones de control están escritas correctamente.

1. **Tipo no válido**

   El tipo de recurso no se encuentra entre los tipos definidos en el archivo WINDOWS. h.

1. **Se esperaba una cadena de texto o un ordinal en el control**

   El campo de *texto* de una instrucción de **control** en la instrucción **Dialog** debe ser una cadena de texto o una referencia ordinal al tipo de control. Si usa un ordinal, asegúrese de que tiene una instrucción `#define` para el control.

1. **Paréntesis no coincidentes**

   Asegúrese de haber cerrado cada paréntesis de apertura en la instrucción de **cuadro de diálogo** .

1. **Valor inesperado en RCData**

   Los valores de *datos sin procesar* de la instrucción **RCDATA** deben ser enteros o cadenas, separados por una coma. Compruebe que no olvidó una coma o unas comillas de una cadena.

1. **Subtipo de menú desconocido**

   El campo *Item-Definition* de la instrucción de **menú** solo puede contener instrucciones **MenuItem** y **popup** .