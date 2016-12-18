---
title: "Novedades de Visual C++ en Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 1cc09fad-85a2-43c2-b022-bb99f5fe0ad7
caps.latest.revision: 101
caps.handback.revision: 101
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Novedades de Visual C++ en Visual Studio 2015
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En Visual Studio 2015, el compilador de C\+\+ y la biblioteca estándar se actualizaron con compatibilidad mejorada con C\+\+11 y compatibilidad inicial con ciertas características C\+\+14.  También incluyen compatibilidad preliminar con ciertas características que se esperaba que estuvieran contenidas en el estándar C\+\+17.  
  
 Asimismo, hemos agregado plantillas de proyecto para el desarrollo de varios dispositivos multiplataforma en [Android e iOS](../Topic/Visual%20C++%20for%20Cross-Platform%20Mobile%20Development.md), hemos introducido varias mejoras de [diagnóstico](#BK_Diagnostics) y [productividad](#BK_IDE), y hemos mejorado considerablemente los [tiempos de compilación](#BK_FasterBuildTimes).  
  
> [!WARNING]
>  En Visual Studio 2015, Visual C\+\+ no se instala de forma predeterminada.  Durante la instalación, asegúrese de elegir la instalación **Personalizada** y luego seleccione los componentes de C\+\+ que desee.  En caso de que Visual Studio ya esté instalado, elija **Archivo &#124; Nuevo &#124; Proyecto &#124; C\+\+** y se le pedirá que instale los componentes necesarios.  
  
 Para obtener información sobre otras novedades de Visual Studio 2015, vea [Novedades de Visual Studio 2015](../Topic/What's%20New%20in%20Visual%20Studio%202015.md).  
  
 En este tema:  
  
1.  [Compilador](#BK_Compiler)  
  
2.  [Biblioteca estándar de C++](#BK_CppStdLib)  
  
3.  [Biblioteca en tiempo de ejecución de C](#BK_CRT)  
  
4.  [Tiempos de compilación más reducidos.](#BK_FasterBuildTimes)  
  
5.  [Rendimiento y calidad del código](#BK_PerfCodeQuality)  
  
6.  [Productividad, depuración y diagnóstico](#BK_IDE)  
  
    1.  [Intellisense de archivo único](#BK_SingleFileIntelliSense)  
  
    2.  [Refactorización](#BK_Refactoring)  
  
    3.  [Mejoras en la base de datos del programa](#BK_PDB)  
  
    4.  [Diagnóstico](#BK_Diagnostics)  
  
7.  [Windows 10 como destino](#BK_Win10)  
  
8.  [Diagnóstico de gráficos](#BK_GraphicsDiagnostics)  
  
9. [Nueva herramienta de uso de la GPU](#BK_GPUUsage)  
  
10. [Nuevas características MFC](#BK_MFC)  
  
## Compatibilidad con los estándares ISO C\/C\+\+  
  
###  <a name="BK_Compiler"></a> Compilador  
  
-   **Funciones reanudables \(resume y await\)** Las palabras clave resume y await proporcionan compatibilidad de nivel de lenguaje para la programación asincrónica y permiten las funciones reanudables.  Actualmente, esta característica sigue en fase experimental y solo está disponible para destinos x64.  **\(Propuesto para C\+\+17 \[N3858\]\)**  
  
-   **Expresiones lambda genéricas \(polimórficas\)** Ahora los tipos de parámetro de función lambda se pueden especificar mediante auto; el compilador interpreta auto en este contexto, de modo que el operador de llamada de función del cierre sea una plantilla de función miembro y que cada uso de auto en la expresión lambda se corresponda con un parámetro de tipo de plantilla distinto.  **\(C\+\+ 14\)**  
  
-   **Expresiones de captura lambda generalizadas** También se denominan init\-capture.  El resultado de una expresión arbitraria ahora puede asignarse a una variable en la cláusula de captura de una expresión lambda.  Esto permite que los tipos de solo movimiento se capturen por valor y permite que una expresión lambda defina miembros de datos arbitrarios en su objeto de cierre.  **\(C\+\+14\)**  
  
-   **Literales binarios** Ahora se admiten literales binarios.  Estos literales tienen el prefijo 0B o 0b y consisten únicamente en los dígitos 0 y 1.  **\(C\+\+14\)**  
  
-   **Deducción del tipo de valor devuelto** Ahora se puede deducir el tipo de valor devuelto de las funciones normales, incluidas las funciones con varias instrucciones return y funciones recursivas.  Estas definiciones de función están precedidas por la palabra clave auto, como en las definiciones de función con un tipo de valor devuelto final, pero se omite el tipo de valor devuelto final.  **\(C\+\+14\)**  
  
-   **decltype\(auto\)** Deducción de tipos mediante la palabra clave auto para inicializar calificadores de referencia de franjas de expresiones y calificadores CV de nivel superior de la expresión.  Decltype\(auto\) conserva los calificadores de referencia y CV y ya puede usarse en cualquier lugar donde pueda usarse auto, excepto para introducir una función con un tipo deducido o con un tipo de valor devuelto final.  **\(C\+\+14\)**  
  
-   **Generación implícita de las funciones de miembro especiales de movimiento** Los operadores de constructores de movimiento y de asignación de movimiento ahora se generan implícitamente cuando las condiciones lo permiten, lo que permite que el compilador cumpla plenamente las referencias rvalue de C\+\+11.  **\(C\+\+11\)**  
  
-   **Heredar constructores** Una clase derivada ahora puede especificar que heredará los constructores de su base de clase \(Base\) incluyendo la instrucción que usa Base::Base; en su definición.  Una clase derivada solo puede heredar todos los constructores de su clase base; no hay manera de que herede solo determinados constructores base.  Una clase derivada no puede heredar de varias clases base si tienen constructores con una firma idéntica, ni puede definir un constructor que tenga una firma idéntica a cualquiera de sus constructores heredados.  **\(C\+\+11\)**  
  
-   **Consultas y control de alineación** Es posible consultar la alineación de una variable mediante el operador alignof\(\) y controlarla mediante el especificador alignas\(\).  alignof\(\) devuelve el límite de bytes en el que se deben asignar las instancias del tipo; para las referencias devuelve la alineación del tipo de referencia, y para las matrices devuelve la alineación del tipo de elemento.  alignas\(\) controla la alineación de una variable; toma una constante o un tipo, donde un tipo es una abreviatura para alignas\(alignof\(type\)\).  **\(C\+\+11\)**  
  
-   **desasignación de tamaño** Los globales  `void operator delete(void *, std::size_t) noexcept` y `void operator delete[](void *, std::size_t) noexcept` ahora se pueden sobrecargar  
  
-   **sizeof extendido** Ahora es posible determinar el tamaño de una variable de miembro de estructura o clase sin una instancia de la estructura o clase mediante usando sizeof\(\).**\(C\+\+11\)**  
  
-   Los **atributos** proporcionan una manera de ampliar la sintaxis de las funciones, variables, tipos y otros elementos del programa sin definir palabras clave nuevas.**\(C\+\+11\)**  
  
-   **constexpr** Cree variables constantes en tiempo de compilación, funciones y tipos definidos por el usuario.  **\(C\+\+11\)**  
  
-   **Literales definidos por el usuario \(UDL\)** Ahora es posible anexar sufijos significativos a los literales numéricos y de cadena para darles tipos de semántica específicos.  El compilador interpreta los literales con sufijo como llamadas al operador UDL adecuado.  **\(C\+\+11\)**  
  
-   **Estática "mágica" segura para subprocesos** Ahora las variables locales estáticas se inicializan de una manera segura para subprocesos, lo que elimina la necesidad de sincronización manual.  Solo la inicialización es segura para subprocesos; todavía debe sincronizarse manualmente el uso de variables locales estáticas por parte de varios subprocesos.  La característica de estática de subprocesos se puede deshabilitar mediante la marca \/Zc:threadSafeInit\- para evitar depender de CRT.  **\(C\+\+11\)**  
  
-   **Almacenamiento local de subprocesos** Use la palabra clave thread\_local para declarar que se debe crear un objeto independiente para cada subproceso.  **\(C\+\+11\)**  
  
-   **noexcept** El operador noexcept ahora puede usarse para comprobar si una expresión puede producir una excepción.  El especificador noexcept ahora puede usarse para especificar que una función no produce excepciones.  **\(C\+\+11\)**  
  
-   **Espacios de nombres incorporados** Ahora se puede especificar un espacio de nombres como incorporado para elevar su contenido al espacio de nombres indicado.  Los espacios de nombres incorporados pueden usarse para crear bibliotecas con versiones que exponen su versión más reciente de forma predeterminada, aunque también ofrecen las versiones anteriores de API explícitamente.  **\(C\+\+11\)**  
  
-   **Uniones sin restricciones** Un tipo de unión ahora puede contener tipos con constructores no triviales.  Se deben definir constructores para dichas uniones.  **\(C\+\+11\)**  
  
-   **Nuevos tipos de caracteres y literales de Unicode** Ahora se admiten los literales de carácter y cadena en UTF\-8, UTF\-16 y UTF\-32 y se incorporaron nuevos tipos de carácter char16\_t y char32\_t.  Los literales de caracteres pueden tener como prefijo u8 \(UTF\-8\), u \(UTF\-16\) o U \(UTF\-32\), como en U'a', mientras que los literales de cadena pueden tener además como prefijo los equivalentes a cadenas sin formato u8R \(cadena sin formato UTF\-8\), uR \(cadena sin formato UTF\-16\) o UR \(cadena sin formato UTF\-32\).  Los nombres de carácter universales pueden usarse libremente en literales de Unicode, como en u'\\u00EF', u8"\\u00EF is i" y u"\\U000000ef is I".  **\(C\+\+11\)**  
  
-   **separadores de dígitos** Se pueden insertar comillas simples a intervalos regulares para facilitar la lectura de literales numéricos largos:  `int x = 1'000'000;` **C\+\+14**  
  
-   **\_\_func\_\_** La \_\_func\_\_ de identificador predefinido se define implícitamente como una cadena que contiene el nombre no completo y sin adornar de la función de inclusión.  
  
-   **\_\_restrict \_\_** Ahora se puede aplicar restrict a las referencias.  
  
###  <a name="BK_CppStdLib"></a> Biblioteca estándar de C\+\+  
  
-   **Literales definidos por el usuario \(UDL\) para tipos de biblioteca estándar** Los encabezados \<chrono\>, \<string\> y \<complex\> ahora proporcionan operadores UDL para su comodidad.  Por ejemplo, 123ms significa std::chrono::milliseconds\(123\), "hello"s significa std::string\("hello"\) y 3.14i significa std::complex\(0.0, 3.14\).  
  
-   **Iteradores hacia delante null** La biblioteca estándar ahora permite la creación de iteradores hacia delante que no hacen referencia a una instancia del contenedor.  Estos iteradores se inicializan con un valor y son iguales para un tipo de contenedor determinado.  La comparación de un iterador que se inicializa con valor y de un iterador que no se inicializa con un valor es indefinida.  **\(C\+\+14\)**  
  
-   **quoted\(\)** La biblioteca estándar ahora es compatible con la función quoted\(\) para facilitar el trabajo con valores de cadena entre comillas y E\/S.  Con quoted\(\), toda una cadena entre comillas se trata como una sola entidad \(ya que las cadenas de caracteres sin espacios en blanco están en secuencias de E\/S\); además, las secuencias de escape se conservan en operaciones de E\/S.  **\(C\+\+14\)**  
  
-   **Búsqueda asociativa heterogénea** La biblioteca estándar ahora es compatible con funciones de búsqueda heterogénea en los contenedores asociativos.  Dichas funciones permiten la búsqueda por tipos distintos de key\_type, siempre y cuando el tipo sea comparable con key\_type.  **\(C\+\+14\)**  
  
-   **Secuencias de enteros en tiempo de compilación** La biblioteca estándar ahora es compatible con el tipo integer\_sequence que representa una secuencia de valores enteros que se pueden evaluar en tiempo de compilación para que sea más fácil trabajar con paquetes de parámetros y para simplificar ciertos patrones de programación de la plantilla.  **\(C\+\+14\)**  
  
-   **exchange\(\)** La biblioteca estándar ahora es compatible con la función de utilidad std::exchange\(\) para asignar un nuevo valor a un objeto y devuelve su valor anterior.  Para los tipos complejos, exchange\(\) evita copiar el valor anterior cuando está disponible un constructor de movimiento, evita copiar el valor nuevo si es temporal o si se mueve, y acepta cualquier tipo como el valor nuevo, aprovechando cualquier operador de asignación y conversión.  **\(C\+\+14\)**  
  
-   **equal\(\), is\_permutation\(\) y mismatch\(\) de doble intervalo** La biblioteca estándar ahora admite las sobrecargas para std::equal\(\), std::is\_permutation\(\) y std::mismatch\(\) que aceptan dos intervalos.  Estas sobrecargas comprueban que las dos secuencias tienen la misma longitud, lo que elimina esta responsabilidad del código de llamada; para las secuencias que no son compatibles con los requisitos de un iterador aleatorio, estas sobrecargas comprueban la longitud mientras comparan los elementos, lo que resulta más eficaz.  **\(C\+\+14\)**  
  
-   **get\<T\>\(\)** La biblioteca estándar ahora es compatible con la función de plantilla get\<T\>\(\) para permitir que los elementos de tupla sean llamados por su tipo.  Si una tupla contiene dos o más elementos del mismo tipo get\<T\>\(\), ese tipo no puede llamar a la tupla, pero todavía se puede llamar a otros elementos escritos de forma exclusiva.  **\(C\+\+14\)**  
  
-   **tuple\_element\_t** La biblioteca estándar ahora es compatible con el alias de tipo tuple\_element\_t\<I, T\> que es un alias para el nombre de tipo tuple\_element\<I, T\>::type.  Esto proporciona cierta comodidad para los programadores de plantillas, ya que es similar a los otros alias de tipo metafunción de \<type\_traits\>.  **\(C\+\+14\)**  
  
-   **Especificación técnica "V3" del sistema de archivos** La implementación incluida de la especificación técnica del sistema de archivos se actualizó a la versión 3 de la especificación.  \[N3940\]  
  
-   **Asignadores mínimos** La biblioteca estándar ahora es plenamente compatible con la interfaz del asignador mínimo; entre las correcciones importantes se incluyen std::function, shared\_ptr, allocate\_shared\(\) y basic\_string.  **\(C\+\+11\)**  
  
-   **\<chrono\>** Se corrigieron los tipos chrono high\_resolution\_clock y steady\_clock.  **\(C\+\+11\)**  
  
-   **N2761 Tipos atómicos en los controladores de señal \(C\+\+11\)**  
  
-   **N3922 Nuevas reglas para auto con listas de inicialización entre llaves \(C\+\+17\)**  
  
-   **N4051 typename en parámetros de plantilla \(C\+\+17\)**  
  
-   **N4259 std::uncaught\_exceptions\(\)**  
  
-   **N4266 Atributos de espacios de nombres y enumeradores**  
  
-   **N4267 Literales de caracteres de u8**  
  
###  <a name="BK_CRT"></a> Biblioteca en tiempo de ejecución de C  
 **Refactorización de la biblioteca CRT**El CRT se ha refactorizado en dos partes.  El **CRT universal** contiene el código que implementa la biblioteca estándar de C en tiempo de ejecución.  Vcruntime140.dll \(o .lib\) contiene un código específico de la versión para iniciar el proceso y controlar las excepciones.  El CRT universal tiene una API estable, por lo que se puede usar sin cambiar el número de versión en cada versión de Visual Studio.  Ahora es un componente del sistema operativo Windows servido por Windows Update.  Ya está instalado en Windows 10.  Puede usar el paquete redistribuible de Visual C\+\+ \(vcredist\) para distribuirlo con las aplicaciones para las versiones anteriores de Windows.  
  
 **La conformidad de C99** [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] implementa por completo la biblioteca estándar de C99, con la excepción de las características de biblioteca que dependen de las características del compilador aún no admitidas por el compilador de Visual C\+\+ \(por ejemplo, no se implementa \<tgmath.h\>\).  
  
 **Rendimiento** Se ha refactorizado gran parte de la biblioteca para simplificar el uso de macros de archivos de encabezado.  Así, se aceleran la compilación e IntelliSense, a la vez que mejora la legibilidad.  Además, se han reescrito muchas funciones de Studio para cumplir estándares y mejorar el rendimiento.  
  
### Cambios importantes  
 Esta compatibilidad mejorada con las normas ISO C\/C\+\+ puede necesitar cambios en el código existente para que se ajuste a C\+\+11 y C99, y se compile correctamente en Visual Studio 2015.  Para obtener más información, vea la sección [Cambios importantes en Visual C\+\+ 2015](../porting/visual-cpp-change-history-2003-20151.md).  
  
 La clase concurrency::task y los tipos relacionados en ppltasks.h ya no se basan en el tiempo de ejecución de ConcRT.  Ahora usan el grupo de subprocesos de Windows como programador.  Este solo afecta al código que usa las primitivas de sincronización ConcRT en operaciones concurrency::task.  Este código debe usar en su lugar las primitivas de sincronización de Windows.  
  
 Asimismo, las primitivas de sincronización de STL ya no se basan en ConcRT.  Para evitar los interbloqueos, no use las primitivas de sincronización de STL en funciones como **concurrency::parallel\_for** o con los tipos de agente asincrónico de PPL.  
  
##  <a name="BK_FasterBuildTimes"></a> Tiempos de compilación más reducidos.  
  
-   **Generación de código en tiempo de vínculo \(LTCG\) incremental** La vinculación incremental ahora puede usarse junto con LTCG para reducir los tiempos de vínculo de las aplicaciones que usan LTCG.  Active esta característica a través de los modificadores del vinculador \/LTCG:incremental y \/LTCG:incremental\_rebuild.  \\  
  
-   **Vinculación incremental para bibliotecas estáticas** Los cambios en las bibliotecas estáticas a las que hacen referencia otros módulos de código ahora se vinculan de forma incremental.  
  
-   **\/Debug:FastLink** Reduce sustancialmente los tiempos de vínculo mediante las nuevas técnicas de creación de PDB.  
  
-   Se realizaron mejoras algorítmicas en el vinculador para reducir los tiempos de vínculo.  
  
-   Se introdujeron mejoras que permiten compilar código denso de plantilla mucho más rápido.  
  
-   **Instrumentación rápida de la Optimización guiada por perfiles \(PGO\)** Se implementó en PGO un nuevo modo de instrumentación ligera para juegos y sistemas en tiempo real.  Junto con otras características nuevas que se ponen a disposición a través de los modificadores del vinculador \/GENPROFILE y \/FASTGETPROFILE, ahora se puede equilibrar la calidad del código y la velocidad de compilación cuando se usa PGO.  
  
-   **Reducción del tamaño de los archivos objeto** Las mejoras en la biblioteca estándar de C\+\+ y en el compilador dan como resultado archivos objeto y bibliotecas estáticas considerablemente más pequeños.  Estas mejoras no afectan al tamaño de las bibliotecas de vínculos dinámicos \(DLL\) o archivos ejecutables \(exe\), ya que el vinculador eliminó históricamente el código redundante.  
  
##  <a name="BK_PerfCodeQuality"></a> Rendimiento y calidad del código  
  
-   **Mejoras en la vectorización automática** Ahora se incluye la vectorización del flujo de control \(if\-then\-else\), la vectorización al compilar en \/O1 \(minimizar tamaño\) y mejoras en la calidad general del código de vector, incluida la compatibilidad con STL paralelas, la vectorización más basada en intervalos para los bucles y la compatibilidad con \#pragma loop\(ivdep\).  
  
-   **Mejoras en la optimización escalar** Mejor generación de código de operaciones de prueba de bits, combinación del flujo de control y optimizaciones \(bucle si se conmuta\) y otras optimizaciones escalares \(por ejemplo, mejor generación de código para std::min y std::max\).  
  
-   **Optimización guiada por perfiles \(PGO\)** Se realizaron varias mejoras en PGO, entre las que se incluyen los conjuntos de referencias mejorados, las mejores capacidades de diseño de datos, la capacidad de reusar inserciones realizadas previamente, la velocidad frente al  tamaño y las decisiones de diseño.  
  
##  <a name="BK_IDE"></a> Productividad, depuración y diagnóstico  
  
###  <a name="BK_SingleFileIntelliSense"></a> Intellisense de archivo único  
 Ahora obtendrá IntelliSense cuando abra un solo archivo de código fuente en el editor, sin necesidad de abrir un archivo de proyecto.  
  
###  <a name="BK_Refactoring"></a> Refactorización  
 Hemos agregado compatibilidad con la refactorización de C\+\+ con las siguientes características:  
  
-   **Cambiar el nombre de símbolo** Cambia todas las apariciones de un símbolo con un nombre nuevo.  
  
-   **Función extracción** Mueve el código seleccionado a su propia función.  Esta refactorización está disponible como extensión de Visual Studio en la Galería de Visual Studio.  
  
-   **Implementar virtuales puros** Genera definiciones de función para las funciones virtuales puras heredadas por una clase o estructura.  Se admite la herencia recursiva y múltiple.  Active esta factorización desde la definición de clase heredada para implementar todas las funciones virtuales puras heredadas, o desde un especificador de clase base para implementar funciones virtuales puras solo de esa clase base.  
  
-   **Crear declaración o definición** Genera una declaración a partir de una definición existente o una definición predeterminada de una declaración existente.  Acceda a esta refactorización desde la declaración o definición existentes, o desde el indicador de bombilla.  
  
-   **Definición de la función de movimiento** Mueve el cuerpo de una función entre los archivos de encabezado y código fuente.  Active esta refactorización desde la firma de la función.  
  
-   **Convertir en literal de cadena sin formato** Convierte una cadena que contiene secuencias de escape en un literal de cadena sin formato.  Las secuencias de escape admitidas son \\\\ \(barra diagonal inversa\), \\n \(nueva línea\), \\t \(tabulación\), \\' \(comillas sencillas\), \\" \(comillas dobles\) y \\?  \(signo de interrogación\).  Active esta característica haciendo clic con el botón secundario en cualquier lugar dentro de una cadena.  
  
 Buscar en archivos se ha mejorado al permitir que los resultados siguientes se anexen a los resultados anteriores; los resultados acumulados pueden eliminarse.  
  
 **Mejoras en la legibilidad de IntelliSense** Las instancias de plantilla y las definiciones de tipo complejas se simplificaron en la ayuda de parámetros y en información rápida para facilitar su lectura.  
  
###  <a name="BK_PDB"></a> Mejoras en la base de datos del programa  
  
-   Se mejoró la velocidad de exploración de soluciones, especialmente para soluciones de gran tamaño.  
  
-   Las operaciones como Ir a definición ya no se bloquean durante la exploración de soluciones, excepto durante la exploración de soluciones inicial, cuando se abre una nueva solución por primera vez.  
  
##  <a name="BK_Diagnostics"></a> Diagnóstico  
  
1.  **Visualizaciones del depurador** Agregue las visualizaciones del depurador Natvis a su proyecto de Visual Studio para facilitar la administración y la integración del control de código fuente.  Los archivos Natvis se pueden editar y guardar durante una sesión de depuración; el depurador adoptará automáticamente los cambios.  Para obtener más información, vea esta [entrada de blog](http://blogs.msdn.com/b/vcblog/archive/2014/06/12/project-support-for-natvis.aspx).  
  
2.  **Diagnóstico de memoria nativo**  
  
    1.  **Sesiones de diagnóstico de memoria** \(Ctrl\+Alt\+F2\) permite supervisar el uso dinámico de la memoria por parte de la aplicación nativa durante una sesión de depuración.  
  
    2.  **Instantáneas de memoria** Capture una imagen momentánea del contenido del montón de la aplicación.  Es posible examinar las diferencias en el estado del montón si se comparan dos instantáneas de memoria.  Vea los tipos de objeto, los valores de instancia y las pilas de llamadas de asignación de cada instancia después de detener la aplicación.  Vea el árbol de llamadas por marco de pila para cada instantánea.  
  
3.  **Detección de interbloqueo y recuperación mejoradas** Al llamar a funciones de C\+\+ desde las ventanas Inspección e Inmediato.  
  
4.  **Diagnóstico de compilador mejorado** El compilador proporciona advertencias mejoradas sobre código sospechoso.  Se agregaron nuevas advertencias \(por ejemplo, variables sombreadas y cadenas de formato printf no coincidentes\).  Se expresaron con más claridad los mensajes de advertencia existentes.  
  
5.  **La marca \/Wv** Las advertencias introducidas después de una versión específica del compilador XX.YY.ZZZZ pueden deshabilitarse mediante la marca \/Wv:XX.YY.ZZZZ.  Pueden deshabilitarse específicamente otras advertencias, además de las especificadas mediante la marca \/Wv.  
  
6.  **Compatibilidad mejorada para depurar código optimizado** Depure código con las marcas \/Zi, \/Zo o \/Z7 habilitadas.  
  
##  <a name="BK_Win10"></a> Windows 10 como destino  
 Visual Studio admite ahora Windows 10 como plataforma de destino en C\+\+.  Las nuevas plantillas de proyecto para el desarrollo de aplicaciones Windows universales admiten como destino los dispositivos de Windows 10: equipos de escritorio, teléfonos móviles, tabletas, HoloLens y otros dispositivos.  Para obtener más información, vea [Crear una aplicación "hello world" en C\+\+ \(Windows 10\)](https://msdn.microsoft.com/es-es/library/windows/apps/dn996906.aspx).  
  
##  <a name="BK_GraphicsDiagnostics"></a> Diagnóstico de gráficos  
 El diagnóstico de gráficos se mejoró con las siguientes características:  
  
-   **Compatibilidad de diagnóstico de gráficos para DirectX12**. La herramienta de diagnóstico de gráficos de Visual Studio ahora admite la depuración de problemas de representación en aplicaciones de DirectX12.  
  
-   **Captura consecutiva** Capture hasta 30 fotogramas consecutivos con una captura.  
  
-   **Captura mediante programación** Inicie la captura de fotogramas mediante programación.  La captura mediante programación es especialmente útil para depurar los sombreadores de cálculo en programas que nunca llaman a Present o cuando un problema de representación es difícil de capturar manualmente, pero se puede predecir mediante programación a partir del estado de la aplicación en tiempo de ejecución.  
  
-   **Lista de eventos de gráficos mejorada** Se agregó la nueva vista Llamadas de dibujo, que muestra los eventos capturados y su estado en una jerarquía organizada por Llamadas de dibujo.  Puede expandir las llamadas de dibujo para mostrar el estado del dispositivo en el momento de la llamada a de dibujo y expandir el estado para mostrar los eventos que establecen sus valores.  
  
-   **Soporte técnico para Windows Phone 8.1** El diagnóstico de gráficos ahora es totalmente compatible con la depuración de aplicaciones de Windows Phone 8.1 en el emulador de Windows Phone o en Windows Phone anclado a red.  
  
-   **Análisis de fotogramas de gráficos** Esta herramienta recopila las medidas de rendimiento de los fotogramas capturados; además, realiza un conjunto de experimentos predefinidos que proporcionan información sobre cómo se vería afectado el rendimiento al aplicarse varias técnicas de textura.  El análisis de fotogramas también recopila los contadores de rendimiento del hardware.  
  
-   **UI dedicada para el análisis de gráficos** La nueva ventana del Analizador de gráficos de Visual Studio es un área de trabajo dedicada al análisis de fotogramas de gráficos.  
  
-   **Editar y aplicar el sombreador** Vea el impacto de los cambios en el código del sombreador en un registro capturado sin volver a ejecutar la aplicación.  
  
-   Configure las opciones de captura en Herramientas\-\>Opciones\-\>Diagnóstico de gráficos.  
  
-   Herramienta de línea de comandos para capturar y reproducir fotogramas.  
  
 Para obtener más información, vea [Diagnóstico de gráficos \(Depurar gráficos de DirectX\)](../Topic/Visual%20Studio%20Graphics%20Diagnostics.md).  
  
##  <a name="BK_GPUUsage"></a> Nueva herramienta de uso de la GPU  
 La herramienta de uso de la GPU de Visual Studio 2015 puede usarse para entender el uso de la GPU que hacen las aplicaciones DirectX.  Están disponibles gráficos del tiempo entre fotogramas, la velocidad de fotogramas y la utilización de la GPU mientras se ejecutan las aplicaciones.  Además, al recopilar y analizar datos de uso detallados de la GPU, esta herramienta puede proporcionar información sobre el tiempo de ejecución de la CPU y la GPU de eventos individuales de DirectX y, por tanto, puede ser útil para determinar si la CPU o la GPU son el cuello de botella del rendimiento.  Vea [Uso de GPU](../Topic/GPU%20Usage.md).  
  
##  <a name="BK_MFC"></a> Nuevas características MFC  
 Ahora se puede especificar la manera en que los controles cambian de tamaño y se mueven cuando un usuario modifica el tamaño de un cuadro de diálogo.  Para más información, vea [Diseño dinámico](../mfc/dynamic-layout.md).  
  
## Vea también  
 [Novedades de Visual Studio 2015](../Topic/What's%20New%20in%20Visual%20Studio%202015.md)   
 [Blog del equipo de Visual C\+\+](http://blogs.msdn.com/b/vcblog/)