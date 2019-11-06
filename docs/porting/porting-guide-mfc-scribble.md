---
title: 'Guía de migración: Scribble de MFC'
ms.date: 10/23/2019
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
ms.openlocfilehash: c5e0e8fecd99e4f03077574da7b7fcb3e538762b
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627211"
---
# <a name="porting-guide-mfc-scribble"></a>Guía de migración: Scribble de MFC

Este es el primero de varios temas que presentan el procedimiento de actualización a Visual Studio 2017 de proyectos de Visual Studio C++ que se crearon en versiones anteriores de Visual Studio. Estos temas muestran el proceso de actualización mediante ejemplos, empezando por un proyecto muy simple y pasando a proyectos un poco más complejos. En este tema mostramos todo el proceso de actualización de un proyecto específico, Scribble de MFC. Es una apropiada introducción básica al proceso de actualización de proyectos de C++.

Cada versión de Visual Studio presenta las posibles incompatibilidades que pueden complicar el paso del código de una versión anterior de Visual Studio a una más reciente. A veces los cambios necesarios se encuentran en su código, por lo que debe volver a compilar y actualizar el código, y a veces los cambios necesarios se encuentran en los archivos del proyecto. Cuando abre un proyecto que se creó con una versión anterior de Visual Studio, Visual Studio le pregunta automáticamente si desea actualizar un proyecto o solución a la versión más reciente. Por lo general, estas herramientas solo actualizan los archivos del proyecto, pero no modifican el código fuente.

## <a name="mfc-scribble"></a>Scribble de MFC

Scribble de MFC es un ejemplo muy conocido que se ha incluido en muchas versiones diferentes de Visual C++. Es una sencilla aplicación de dibujo que muestra algunas de las características básicas de MFC. Hay disponibles varias versiones de esta aplicación, incluidas las versiones de código administrado y nativo. En este ejemplo encontramos una versión antigua de Scribble en código nativo de Visual Studio 2005 y la abrimos en Visual Studio 2017.

Antes de actualizar, asegúrese de que tiene instalada la carga de trabajo de escritorio de Windows. Abra el instalador de Visual Studio (vs_installer.exe). Una manera de abrir el instalador consiste en elegir **Archivo** > **Nuevo proyecto** y desplazarse hasta la parte inferior de la lista de plantillas instaladas hasta que vea **Abrir el instalador de Visual Studio**. Después de abrir el instalador, verá todas las cargas de trabajo disponibles. Si la casilla de la carga de trabajo del **Escritorio de Windows** no está seleccionada, selecciónela y haga clic en el botón **Modificar** situado en la parte inferior de la ventana.

Después, realice una copia de seguridad de toda la solución y su contenido.

Por último, abra la solución en la versión más reciente de Visual Studio y permita que el asistente convierta el proyecto. 

Tenga en cuenta que también puede ejecutar devenv en la línea de comandos mediante la opción `/Upgrade`, en lugar de usar el asistente para actualizar los proyectos. Vea [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe). Eso podría ayudar a automatizar el proceso de actualización para un gran número de proyectos.

### <a name="step-1-converting-the-project-file"></a>Paso 1. Convertir el archivo del proyecto

Al abrir un archivo de proyecto antiguo en Visual Studio, Visual Studio ofrece la conversión del archivo de proyecto a la versión más reciente, que aceptamos. Se mostró el siguiente cuadro de diálogo:

![Revisar cambios de proyecto y solución](../porting/media/scribbleprojectupgrade.PNG "Revisar cambios de proyectos y soluciones")

Se produjo un error por el que se nos informaba de que el destino de Itanium no estaba disponible y no se realizaría la conversión.

```Output
Platform 'Itanium' is missing from this project. All the configurations and their file configuration settings specific to this platform will be ignored. If you want this platform converted, please make sure you have the corresponding platform installed under '%vctargetpath%\platforms\Itanium'.Continue to convert this project without this platform?
```

En el momento en que se creó el proyecto de Scribble anterior, Itanium era una plataforma de destino importante. La plataforma Windows ya no admite Itanium, así que decidimos dejar de proporcionar compatibilidad con la plataforma Itanium.

A continuación, Visual Studio mostró un informe de migración de todos los problemas con el antiguo archivo de proyecto.

![Informe de actualización](../porting/media/scribblemigrationreport.PNG "Informe de actualización")

En este caso, todos los problemas eran advertencias y Visual Studio realizó los cambios pertinentes en el archivo del proyecto. La gran diferencia en lo que se refiere al proyecto es que la herramienta de compilación cambió de vcbuild a msbuild. Este cambio se introdujo por primera vez en Visual Studio 2010. Otros de los cambios incluyen una determinada reorganización de la secuencia de elementos en el propio archivo de proyecto. Ninguno de los problemas requirió atención adicional para este proyecto simple.

### <a name="step-2-getting-it-to-build"></a>Paso 2. Hacer que compile

Antes de compilar, comprobamos el conjunto de herramientas de la plataforma para saber qué versión del compilador está utilizando el sistema del proyecto. En el diálogo de propiedades del proyecto, en **Propiedades de configuración**, en la categoría **General**, examine la propiedad **Conjunto de herramientas de la plataforma**. Contiene la versión de Visual Studio y el número de versión de las herramientas de la plataforma, que en este caso es v141 para la versión de Visual Studio 2017 de las herramientas. Al convertir un proyecto que se compiló originalmente con Visual Studio 2010, 2012, 2013 o 2015, el conjunto de herramientas no se actualiza automáticamente al conjunto de herramientas más reciente.

Para realizar el cambio a Unicode, abra las propiedades del proyecto y, en **Propiedades de configuración**, elija la sección **General** y busque la propiedad **Juego de caracteres**. Cambie el valor **Utilizar juego de caracteres multibyte** por **Utilizar juego de caracteres Unicode**. El efecto de este cambio es que ahora las macros _UNICODE y UNICODE están definidas y _MBCS no lo está. Puede comprobarlo en el cuadro de diálogo de propiedades en la categoría **C/C++** , en la propiedad **Línea de comandos**.

```Output
/GS /analyze- /W4 /Zc:wchar_t /Zi /Gm- /Od /Fd".\Debug\vc141.pdb" /Zc:inline /fp:precise /D "_AFXDLL" /D "WIN32" /D "_DEBUG" /D "_WINDOWS" /D "_UNICODE" /D "UNICODE" /errorReport:prompt /WX /Zc:forScope /Gd /Oy- /MDd /Fa".\Debug\" /EHsc /nologo /Fo".\Debug\" /Fp".\Debug\Scribble.pch" /diagnostics:classic
```

Aunque el proyecto Scribble no se configuró para que se compilase con caracteres Unicode, ya estaba escrito con TCHAR en lugar de char, por lo que en realidad no hace falta cambiar nada. El proyecto se compila correctamente con el juego de caracteres Unicode.

Ahora compile la solución. En la ventana de salida, el compilador nos indica que _WINNT32_WINNT no está definida:

```Output
_WIN32_WINNT not defined. Defaulting to _WIN32_WINNT_MAXVER (see WinSDKVer.h)
```

Esto es una advertencia, no un error, y se genera habitualmente al actualizar un proyecto de Visual Studio C++. Esta es la macro que define cuál es la versión más antigua de Windows sobre la que se ejecutará nuestra aplicación. Si omitimos la advertencia, aceptamos el valor predeterminado, _WIN32_WINNT_MAXVER, que significa la versión actual de Windows. Puede ver una tabla con los valores posibles en [Using the Windows Headers](/windows/win32/WinProg/using-the-windows-headers) (Uso de los encabezados de Windows). Por ejemplo, podemos establecer que se ejecute en cualquier versión de Vista en adelante.

```cpp
#define _WIN32_WINNT _WIN32_WINNT_VISTA
```

Si el código utiliza partes de la API de Windows que no están disponibles en la versión de Windows que especifica con esta macro, debería mostrarse como un error del compilador. En el caso del código de Scribble, no hay ningún error.

### <a name="step-3-testing-and-debugging"></a>Paso 3. Pruebas y depuración

No hay ningún conjunto de pruebas, por lo que simplemente iniciamos la aplicación y probamos sus funciones manualmente mediante la interfaz de usuario. No se observó ningún problema.

### <a name="step-4-improve-the-code"></a>Paso 4. Mejorar el código

Ahora que ha migrado a Visual Studio 2017, puede que quiera realizar algunos cambios para aprovechar las nuevas características de C++. La versión actual del Compilador de Microsoft Visual C++ presenta mayor compatibilidad con el estándar de C++ que las anteriores, así que si tiene previsto hacer cambios en el código para que sea más seguro y portátil con respecto a otros compiladores y sistemas operativos, debería pensar en efectuar algunas mejoras.

## <a name="next-steps"></a>Pasos siguientes

Scribble era una aplicación de escritorio pequeña y simple de Windows, y no fue difícil de convertir. Muchas aplicaciones pequeñas y sencillas son fáciles de convertir a la nueva versión.  Sin embargo, será necesario más tiempo para actualizar aplicaciones más complejas, con muchas más líneas de código, antiguo código heredado que podría no estar a la altura de los estándares de ingeniería modernos, varios proyectos y bibliotecas, o pasos de compilación personalizados, así como para actualizar aplicaciones con compilaciones complejas automatizadas mediante script. Vaya al [siguiente ejemplo](../porting/porting-guide-com-spy.md), una aplicación ATL/COM llamada COM Spy.

## <a name="see-also"></a>Vea también

[Migración y actualización: ejemplos y casos prácticos](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Ejemplo siguiente: COM Spy](../porting/porting-guide-com-spy.md)
