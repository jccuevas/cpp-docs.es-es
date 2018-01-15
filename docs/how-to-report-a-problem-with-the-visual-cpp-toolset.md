---
title: "Cómo notificar un problema con el conjunto de herramientas de Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 1/03/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1a5cdb873d536702ecf8536d9a9e7c0205cc923
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset"></a>Cómo notificar un problema con el conjunto de herramientas de Visual C++

Si tiene problemas con el compilador, el enlazador u otras herramientas de Visual C++, nos gustaría que nos informara de ello.

La mejor manera de comunicarnos un problema consiste en enviarnos un informe que incluya una descripción del problema que ha encontrado, detalles sobre cómo está compilando el programa y algo de código que podamos usar para reproducir el problema en nuestras máquinas. Esta información nos permite comprobar rápidamente que el problema existe y que no es local de su entorno, determinar si afecta a otras versiones del compilador y diagnosticar la causa.

En este documento, podrá obtener información sobre lo siguiente:

- [Cómo preparar un informe](#prepare) de calidad.

- [Cómo generar una reproducción](#generate) y los distintos tipos de reproducciones.

- [Las maneras de enviar el informe](#send) y en qué se diferencian.

Sus informes son importantes para nosotros y para otros desarrolladores como usted. Gracias por ayudarnos a mejorar Visual C++.

## <a name="prepare"></a> Cómo preparar un informe

Es importante crear un informe de alta calidad, ya que resulta muy difícil reproducir el problema que ha encontrado en la máquina si no aporta información completa. Cuanto mejor sea su informe, más eficazmente podremos recrear y diagnosticar el problema.

Como mínimo, el informe debe contener lo siguiente:

- Información de versión completa sobre el conjunto de herramientas que está usando.

- La línea de comandos cl.exe completa usada para compilar el código.

- Una descripción detallada del problema que se ha encontrado.

- Una reproducción, es decir, código fuente que muestre el problema.

Siga leyendo para conocer qué información específica necesitamos y dónde puede encontrarla.

### <a name="the-toolset-version"></a>La versión del conjunto de herramientas

Necesitamos la información de versión completa del conjunto de herramientas que está usando para que podamos probar la reproducción con ese mismo conjunto de herramientas en nuestras máquinas. Si podemos reproducir el problema, esta información también nos dará un punto de partida para investigar en qué otras versiones del conjunto de herramientas se produce el mismo problema.

#### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>Para informar sobre la versión completa del compilador que está usando

1. Presione la tecla Windows del teclado y empiece a escribir `Developer Command Prompt`.

1. Seleccione la versión del **Símbolo del sistema para desarrolladores** que coincida con su versión de Visual Studio cuando aparezca en la lista de coincidencias.

1. En la consola del **Símbolo del sistema para desarrolladores**, escriba el comando `cl /Bv /CLR`.

La salida debe tener un aspecto similar a este:

```Output
C:\Compiler>cl /Bv /CLR
Microsoft (R) C/C++ Optimizing Compiler Version 18.00.40209
for Microsoft (R) .NET Framework version 4.00.30319.34014
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\WinCComp\binaries.x86chk\bin\i386\cl.exe:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c1.dll:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c1xx.dll:      Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c2.dll:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\link.exe:      Version 12.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\mspdb120.dll:  Version 12.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\1033\clui.dll: Version 18.00.40209.0
 Common Language Runtime:                            Version  4.00.30319.34014

cl : Command line error D8003 : missing source filename
```

Copie y pegue toda la salida en el informe.

### <a name="the-command-line"></a>La línea de comandos

Necesitamos la línea de comandos completa (cl.exe y sus argumentos) que se ha usado en la compilación del código para que podamos compilarlo exactamente del mismo modo en nuestras máquinas. Esto es importante porque el problema que se ha encontrado podría existir únicamente al compilar con un argumento determinado o con una combinación de argumentos determinada.

El mejor lugar para encontrar esta información es el registro de compilación inmediatamente después de experimentar el problema. Esto garantiza que la línea de comandos contiene exactamente los mismos argumentos que podrían contribuir al problema.

#### <a name="to-report-the-contents-of-the-command-line"></a>Para informar sobre el contenido de la línea de comandos

1. Busque el archivo **CL.command.1.tlog** y ábralo. De forma predeterminada, este archivo se encuentra en \\...\Visual Studio *version*\Projects\\*SolutionName*\\*ProjectName*\Config\\*ProjectName*.tlog\CL.command.1.tlog.

   En este archivo, encontrará los nombres de los archivos de código fuente seguidos de los argumentos de la línea de comandos que se han usado para compilarlos, cada uno en líneas independientes.

1. Busque la línea que contiene el nombre del archivo de código fuente donde se produce el problema; la línea inferior contiene el comando cl.exe correspondiente y sus argumentos.

Copie y pegue toda la línea de comandos en el informe.

### <a name="a-description-of-the-problem"></a>Una descripción del problema

Necesitamos una descripción detallada del problema que se ha encontrado para que podamos comprobar que tiene el mismo efecto en nuestras máquinas. Además, a veces también nos ayuda saber qué estaba intentando conseguir y qué esperaba que sucediera.

Proporcione los mensajes de error precisos que muestra el conjunto de herramientas, una breve descripción de lo que estaba intentando conseguir para que entendamos su código de reproducción y otros detalles que puedan ayudarnos a diagnosticar el problema que ha experimentado, como, por ejemplo, las soluciones alternativas que haya encontrado. Evite repetir la información que se encuentra en otro lugar del informe.

### <a name="the-repro"></a>La reproducción

Necesitamos una *reproducción*, es decir, un ejemplo de código fuente autocontenido en el que se muestre el problema que ha encontrado, para que podamos reproducir el error en nuestras máquinas. El tipo de problema que ha experimentado determinará el tipo de reproducción que debe incluir en el informe. Sin una reproducción adecuada, no tenemos nada para investigar.

Puede incluir reproducciones cortas y autocontenidas directamente en el texto del informe, pero para incluir reproducciones de código fuente grandes debe adjuntarlas al informe. Las reproducciones que no se pueden reducir a un solo archivo de código fuente deben empaquetarse. Para ello, comprima en un archivo .zip o similar un directorio que contenga todos los archivos y adjúntelo al informe. Cualquier detalle adicional que sea específico del escenario debe incluirse siempre en el texto del informe, nunca en el código fuente.

El mejor tipo de reproducción que nos puede proporcionar es una *reproducción mínima*. Se trata de un archivo de código fuente único y autocontenido (sin referencias a los encabezados de usuario) que contiene código suficiente para mostrar el problema. Si puede proporcionar una reproducción de este tipo, adjunte el archivo de código fuente al informe; es todo lo que necesitamos.

Si no puede condensar el problema en una reproducción mínima sin dependencias, consulte las secciones siguientes para determinar el tipo de reproducción que debe incluir en el informe.

#### <a name="frontend-parser-crash"></a>Bloqueo de front-end (analizador)

Los bloqueos de front-end se producen durante la fase de análisis del compilador. Normalmente, el compilador emitirá el mensaje [Error irrecuperable C1001](error-messages/compiler-errors-1/fatal-error-c1001.md) y hará referencia al archivo de código fuente y al número de línea en el que se produjo el error. A menudo mencionará un archivo msc1.cpp, pero puede pasar por alto este detalle.

Para este tipo de bloqueo, proporcione una [reproducción preprocesada](#preprocessed-repros).

A continuación se muestra un ejemplo de la salida del compilador para este tipo de bloqueo:

```Output
SandBoxHost.cpp
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        fatal error C1001: An internal error has occurred in the compiler.
(compiler file 'msc1.cpp', line 1369)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        note: This diagnostic occurred in the compiler generated function
        'void Microsoft::Ceres::Common::Tools::Sandbox::SandBoxedProcess::Dispose(bool)'
Internal Compiler Error in d:\o\dev\otools\bin\x64\cl.exe.  You will be prompted
        to send an error report to Microsoft later.
INTERNAL COMPILER ERROR in 'd:\o\dev\otools\bin\x64\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

#### <a name="backend_crash"></a> Bloqueo de back-end (generación de código)

Los bloqueos de back-end se producen durante la fase de generación de código del compilador. Normalmente, el compilador emitirá el mensaje [Error irrecuperable C1001](error-messages/compiler-errors-1/fatal-error-c1001.md) y podría no hacer referencia al archivo de código fuente y al número de línea asociados al problema. A menudo mencionará un archivo compiler\utc\src\p2\main.c, pero puede pasar por alto este detalle.

Para este tipo de bloqueo, proporcione una [reproducción de vínculo](#link-repros) si usa la Generación de código en tiempo de vínculo (LTCG) o una [reproducción preprocesada](#preprocessed-repros) en caso de que no la use. LTGC se habilita mediante el argumento de línea de comandos `/GL` en cl.exe.

A continuación se muestra un ejemplo de la salida del compilador para este tipo de bloqueo en el que **no** se usa LTCG. Si la salida del compilador tiene este aspecto, debe proporcionar una [reproducción preprocesada](#preprocessed-repros).

```Output
repro.cpp
\\officefile\public\tadg\vc14\comperror\repro.cpp(13) : fatal error C1001:
        An internal error has occurred in the compiler.
(compiler file 'f:\dd\vctools\compiler\utc\src\p2\main.c', line 230)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
INTERNAL COMPILER ERROR in
        'C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

Si la línea que empieza por **ERROR INTERNO DEL COMPILADOR** menciona link.exe en lugar de cl.exe, ya se ha habilitado LTCG y debe proporcionar una [reproducción de vínculo](#link-repros). Si en el mensaje de error del compilador no queda claro si se ha habilitado LTCG, puede que tenga que examinar los argumentos de la línea de comandos que copió del registro de compilación en el paso anterior para el argumento de la línea de comandos `/GL`.

#### <a name="linker-crash"></a>Bloqueo del enlazador

Los bloqueos del enlazador se producen durante la fase de vinculación, después de que se haya ejecutado el compilador. Normalmente, el enlazador emitirá el mensaje [Linker Tools Error LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md) (Error de las herramientas del enlazador LNK1000).

> [!NOTE]
> Si la salida menciona C1001 o implica la Generación de código en tiempo de vínculo, vea [Bloqueo de back-end (generación de código)](#backend_crash) para obtener más información.

Para este tipo de bloqueo, proporcione una [reproducción de vínculo](#link-repros).

A continuación se muestra un ejemplo de la salida del compilador para este tipo de bloqueo.

```Output
z:\foo.obj : error LNK1000: Internal error during IMAGE::Pass2

  Version 14.00.22816.0

  ExceptionCode            = C0000005
  ExceptionFlags           = 00000000
  ExceptionAddress         = 00007FF73C9ED0E6 (00007FF73C9E0000)
        "z:\tools\bin\x64\link.exe"
  NumberParameters         = 00000002
  ExceptionInformation[ 0] = 0000000000000000
  ExceptionInformation[ 1] = FFFFFFFFFFFFFFFF

CONTEXT:

  Rax    = 0000000000000400  R8     = 0000000000000000
  Rbx    = 000000655DF82580  R9     = 00007FF840D2E490
  Rcx    = 005C006B006F006F  R10    = 000000655F97E690
  Rdx    = 000000655F97E270  R11    = 0000000000000400
  Rsp    = 000000655F97E248  R12    = 0000000000000000
  Rbp    = 000000655F97EFB0  E13    = 0000000000000000
  Rsi    = 000000655DF82580  R14    = 000000655F97F390
  Rdi    = 0000000000000000  R15    = 0000000000000000
  Rip    = 00007FF73C9ED0E6  EFlags = 0000000000010206
  SegCs  = 0000000000000033  SegDs  = 000000000000002B
  SegSs  = 000000000000002B  SegEs  = 000000000000002B
  SegFs  = 0000000000000053  SegGs  = 000000000000002B
  Dr0    = 0000000000000000  Dr3    = 0000000000000000
  Dr1    = 0000000000000000  Dr6    = 0000000000000000
  Dr2    = 0000000000000000  Dr7    = 0000000000000000
```

Si la vinculación incremental está habilitada y el bloqueo se ha producido únicamente tras la vinculación inicial (es decir, después de la primera vinculación completa en la que se basa la vinculación incremental posterior), proporcione también una copia de los archivos objeto (.obj) y de biblioteca (.lib) que correspondan a los archivos de código fuente modificados tras completar la vinculación inicial.

#### <a name="bad-code-generation"></a>Generación de código no válido

La generación de código no válido es poco frecuente, pero se produce cuando el compilador genera equivocadamente código incorrecto que hará que la aplicación se bloquee en tiempo de ejecución en lugar de detectar este problema en tiempo de compilación. Si cree que el problema que está experimentando provoca la generación de código no válido, considere el informe como si se tratara de un [bloqueo de back-end (generación de código)](#backend_crash).

Para este tipo de bloqueo, proporcione una [reproducción de vínculo](#link-repros) si usa la Generación de código en tiempo de vínculo (LTCG) o una [reproducción preprocesada](#preprocessed-repros) en caso de que no la use. LTGC se habilita mediante el argumento de línea de comandos `/GL` en cl.exe.

## <a name="generate"></a> Generar una reproducción

Una reproducción es un ejemplo de código completo y autocontenido en el que se muestra el problema sobre el que está informando. Una reproducción **no** es un fragmento de código. Debe ser un ejemplo completo que se compila y se ejecuta (o que se compilaría y se ejecutaría de no ser por los errores que produce el problema sobre el que está informando). Debe contener todas las directivas #include necesarias, incluso para los encabezados estándar.

Además, una buena reproducción se caracteriza por lo siguiente:

- **Es mínima.** Las reproducciones deben ser lo más pequeñas posible, pero mostrar exactamente el problema detectado. No es necesario que las reproducciones sean complejas o realistas: lo mejor es que sean simples y concisas. No necesitan incluir ejemplos que muestren el código que funciona, aunque pueden hacerlo si es ilustrativo. Solo es necesario incluir código de ejemplo que cause el problema.

- **Es autocontenida.** Las reproducciones deben evitar las dependencias innecesarias. Si puede reproducir el problema sin bibliotecas de terceros, hágalo. Si puede reproducir el problema sin código de biblioteca (se aceptan `std::out` y `printf()`), hágalo. Nos resulta extremadamente útil que reduzca la cantidad de código que debemos tener en cuenta como posible causante del problema.

- **Tiene la versión más reciente del compilador.** Las reproducciones deben usar la versión más reciente del conjunto de herramientas siempre que sea posible. Muy a menudo, los problemas que todavía pueden producirse en versiones antiguas del conjunto de herramientas se han corregido en las versiones más recientes.

- **Está comprobada con otros compiladores**, si procede. Las reproducciones que implican código C++ portátil deben comprobar su comportamiento con otros compiladores si es posible.

   Este paso ayuda a determinar si el código es correcto (como cuando MSVC discrepa con Clang y GCC) o incorrecto (como cuando MSVC, Clang y GCC están de acuerdo en que el código produce el error).

A continuación se muestran instrucciones para generar los distintos tipos de reproducciones que se usan para notificar los diversos problemas.

### <a name="preprocessed-repros"></a>Reproducciones preprocesadas

Una reproducción preprocesada es un archivo de código fuente único que muestra un problema y que se ha generado a partir de la salida del preprocesador de C mediante el procesamiento del archivo de código fuente original. Este proceso inserta los encabezados incluidos para quitar las dependencias de archivos de encabezado y archivos de código fuente adicionales, y también resuelve las macros, #ifdefs y otros comandos de preprocesador que podrían depender del entorno local.

> [!NOTE]
> Tenga en cuenta que las reproducciones preprocesadas son menos adecuadas para los problemas que podrían ser consecuencia de errores de la implementación de biblioteca estándar, porque a menudo se sustituye la implementación más reciente en curso para ver si se ha corregido el problema. En este caso, no preprocese la reproducción y, si no puede reducir el problema a un solo archivo de código fuente, empaquete el código en un archivo .zip o similar, o bien considere la posibilidad de usar una reproducción de proyecto IDE (vea más abajo [Otras reproducciones](#other-repros)).

#### <a name="to-preprocess-a-source-code-file"></a>Para preprocesar un archivo de código fuente

1. Presione la tecla Windows del teclado y empiece a escribir `Developer Command Prompt`.

1. Seleccione la versión del **Símbolo del sistema para desarrolladores** que coincida con su versión de Visual Studio cuando aparezca en la lista de coincidencias.

1. En la ventana de la consola del **Símbolo del sistema para desarrolladores**, escriba el comando `cl /P argumentsfilename.cpp`.

Cuando tenga el archivo preprocesado (ahora denominado filename.i), es recomendable que se asegure de que el problema todavía se reproduce con el archivo preprocesado. Puede usar el argumento de la línea de comandos `/TP` para indicar a cl.exe que omita el paso del preprocesador e intente compilar como de costumbre.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Para confirmar que el error todavía se reproduce con el archivo preprocesado

1. Presione la tecla Windows del teclado y empiece a escribir `Developer Command Prompt`.

1. Seleccione la versión del **Símbolo del sistema para desarrolladores** que coincida con su versión de Visual Studio cuando aparezca en la lista de coincidencias.

1. En la ventana de la consola del **Símbolo del sistema para desarrolladores**, escriba el comando `cl arguments /TP filename.i`.

1. Confirme que el problema se reproduce.

Por último, adjunte esta reproducción al informe.

### <a name="link-repros"></a>Reproducciones de vínculo

Una reproducción de vínculo es un único directorio que contiene los artefactos de compilación que, en conjunto, muestran un problema que se produce en tiempo de vínculo, como un bloqueo de back-end relacionado con la Generación de código en tiempo de vínculo (LTCG) o un bloqueo del enlazador. Los artefactos de compilación incluidos son los necesarios como entrada del enlazador para que se pueda reproducir el problema. Las reproducciones de vínculo se pueden crear fácilmente mediante las funciones que proporciona el enlazador.

#### <a name="to-generate-a-link-repro"></a>Para generar una reproducción de vínculo

1. Abra un símbolo del sistema y escriba el comando `mkdir directory` para crear un directorio para la reproducción de vínculo.

1. Establezca la variable de entorno link_repro en el directorio que acaba de crear y escriba el comando `set link_repro=directory`.

1. Si quiere realizar la compilación desde Visual Studio, inícielo desde el símbolo del sistema. Para ello, escriba el comando `devenv`. De este modo se garantiza que el valor de la variable de entorno link_repro esté visible en Visual Studio.

1. Compile la aplicación y confirme que el problema esperado se ha producido.

1. Cierre ahora Visual Studio si lo inició en el paso 3.

1. Borre la variable de entorno link_repro y escriba el comando `set link_repro=`.

Por último, comprima todo el directorio en un archivo .zip o similar para empaquetar la reproducción y adjúntelo al informe.

### <a name="other-repros"></a>Otras reproducciones

Si no es posible reducir el problema a un solo archivo de código fuente o reproducción preprocesada y el problema no requiere una reproducción de vínculo, podemos investigar un proyecto IDE. El código incluido en el proyecto también debe ser mínimo y se le aplican todas las instrucciones de este documento.

Cree la reproducción como un proyecto IDE mínimo, comprima toda la estructura de directorios en un archivo .zip o similar para empaquetarlo y adjúntelo al informe.

## <a name="send"></a> Maneras de enviar el informe

Puede enviarnos el informe de varias maneras. Puede usar la [herramienta integrada Notificar un problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) de Visual Studio o las páginas de la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/). También es posible enviar un correo electrónico con el informe, pero es preferible utilizar los dos primeros métodos. El hecho de elegir una opción u otra dependerá del grado de interacción que quiera tener con los ingenieros que se encargarán de investigar el informe y de si quiere llevar un seguimiento del progreso o compartir el informe con la comunidad.

> [!NOTE]
> Independientemente de cómo envíe el informe, Microsoft respeta su privacidad. Para obtener información sobre cómo tratamos los datos que nos envía, vea la [Declaración de privacidad de la familia de productos de Microsoft Visual Studio](https://www.visualstudio.com/dn948229).

### <a name="use-the-report-a-problem-tool"></a>Usar la herramienta Notificar un problema

La herramienta **Notificar un problema** de Visual Studio permite a los usuarios de Visual Studio informar sobre diversos problemas en pocos clics. Proporciona un formulario sencillo que puede usar para especificar información detallada sobre el problema que ha encontrado y enviar el informe sin tener que salir del IDE.

Informar de un problema a través de la herramienta **Notificar un problema** del entorno de desarrollo integrado es fácil y útil. Para acceder a ella, elija el icono **Enviar comentarios** que encontrará junto al cuadro de búsqueda **Inicio rápido** de la barra de título. También la encontrará en la barra de menú, en **Ayuda** > **Enviar comentarios** > **Notificar un problema**.

Si elige informar de un error, primero intente encontrar problemas similares en la comunidad de desarrolladores. Si hay alguien que ya ha informado del problema en cuestión, vote a favor del tema y agregue sus comentarios con más detalles al respecto. Si no encuentra ningún problema similar, haga clic en **Informar de un problema nuevo**, en la parte inferior del cuadro de diálogo de Comentarios de Visual Studio, y siga los pasos para notificar el problema.

### <a name="use-the-visual-studio-developer-community-pages"></a>Uso de las páginas de la comunidad de desarrolladores de Visual Studio

Las páginas de la comunidad de desarrolladores de Visual Studio son otra forma muy útil de informar de problemas y encontrar soluciones para Visual Studio, el compilador de C++, las herramientas y las bibliotecas. En la página [Preguntas de Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html) puede informar de problemas con el entorno de desarrollo integrado o la instalación. En el caso de problemas relacionados con el compilador de C++, el enlazador y otras herramientas y bibliotecas, use la página [Preguntas de C++](https://developercommunity.visualstudio.com/spaces/62/index.html).

En el banner de la comunidad de desarrolladores que encontrará cerca de la parte superior de cada página verá un cuadro de búsqueda que puede utilizar para encontrar publicaciones o temas en los que se informa de problemas similares. Es posible que ya esté disponible una solución u otra información útil relacionada con su problema en un tema existente. Si alguien ya ha notificado el mismo problema, vote a favor del tema y escriba su comentario en él, en lugar de crear otro tema sobre lo mismo.

Si todavía nadie ha informado del problema, haga clic en el botón **Notificar un problema** que encontrará junto al cuadro de búsqueda de la página de la comunidad de desarrolladores. Es posible que se le solicite que inicie sesión en su cuenta de Visual Studio y acepte ofrecer acceso a su perfil a la aplicación de la comunidad de desarrolladores. Una vez que haya iniciado sesión, vaya directamente a la página desde la que puede informar del problema. Puede incluir el código y la línea de comandos para reproducir el problema, capturas de pantalla, vínculos a debates relacionados y cualquier otra información que crea útil y oportuna.

### <a name="send-an-email"></a>Enviar un correo electrónico

Otra manera de enviar un informe directamente al equipo de Visual C++ es por correo electrónico. Puede ponerse en contacto nosotros en [compilercrash@microsoft.com](mailto:compilercrash@microsoft.com). Use este método solo si los otros dos no están disponibles, ya que el correo electrónico no se supervisa con tanta atención como los problemas notificados en la comunidad de desarrolladores mediante la herramienta **Notificar un problema** o las páginas web. Además, el resto de usuarios de Visual Studio no podrán consultar los comentarios ni las soluciones.

Si decide enviar el informe por correo electrónico, puede usar la plantilla siguiente como cuerpo del mensaje. No olvide adjuntar código fuente u otros archivos si no incluye dicha información en el cuerpo del correo electrónico.

```Example
To: compilercrash@microsoft.com
Subject: Visual C++ Error Report
-----

Compiler version:

CL.EXE command line:

Problem description:

Source code and repro steps:

```

> [!TIP]
> En el caso de otros tipos de problemas en Visual Studio que no estén relacionados con el conjunto de herramientas (por ejemplo, problemas de la interfaz de usuario, funciones del IDE interrumpidas o bloqueos generales), la herramienta Notificar un problema puede ser una opción especialmente buena debido a sus funciones de captura de pantalla y su capacidad de grabar las acciones de la interfaz de usuario que producen el problema en cuestión. Nunca debe notificar sobre estos otros tipos de errores mediante el envío de un correo electrónico a compilercrash@microsoft.com.

