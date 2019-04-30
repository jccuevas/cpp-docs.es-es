---
title: Versiones de la biblioteca MFC
ms.date: 1/09/2018
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
ms.openlocfilehash: c0dc724566063066175ea54e2b7734892e3c6e05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62238512"
---
# <a name="mfc-library-versions"></a>Versiones de la biblioteca MFC

La biblioteca MFC está disponible en las versiones compatibles con ANSI byte único y del juego de caracteres multibyte (MBCS) código, así como las versiones que admiten Unicode (codificada como UTF-16LE, el juego de caracteres nativo de Windows). Cada versión MFC está disponible como una biblioteca estática o como un archivo DLL compartido. También hay una versión más pequeña de biblioteca estática de MFC que sale de los controles MFC para cuadros de diálogo, para las aplicaciones que son muy sensibles al tamaño y no necesitan esos controles. Las bibliotecas MFC están disponibles en ambas versiones de depuración y versión para las arquitecturas compatibles que incluyen x86, x64 y procesadores ARM. Puede crear ambas aplicaciones (archivos .exe) y archivos DLL con cualquier versión de las bibliotecas MFC. Hay también un conjunto de bibliotecas MFC compiladas para interactuar con código administrado. Archivos DLL MFC compartidos incluyen un número de versión para indicar la compatibilidad binaria de la biblioteca.

## <a name="automatic-linking-of-mfc-library-versions"></a>Vinculación automática de versiones de la biblioteca MFC

Los archivos de encabezado MFC determinan automáticamente la versión correcta de la biblioteca MFC para crear un vínculo, según los valores definidos en el entorno de compilación. Los archivos de encabezado MFC agregan directivas de compilador que indican al vinculador para vincular en una versión específica de la biblioteca MFC.

Por ejemplo, el AFX. Archivo de encabezado H indica al vinculador vincule la estática completo, limitada static o shared versión DLL de MFC; Versión ANSI/MBCS o Unicode. y la versión comercial o de depuración, dependiendo de la configuración de compilación:

```cpp
#ifndef _AFXDLL
    #ifdef _AFX_NO_MFC_CONTROLS_IN_DIALOGS
        #ifdef _DEBUG
            #pragma comment(lib, "afxnmcdd.lib")
        #else
            #pragma comment(lib, "afxnmcd.lib")
        #endif
        #pragma comment(linker, "/include:__afxNoMFCControlSupportInDialogs")
        #pragma comment(linker, "/include:__afxNoMFCControlContainerInDialogs")
    #endif
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "nafxcwd.lib")
        #else
            #pragma comment(lib, "nafxcw.lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "uafxcwd.lib")
        #else
            #pragma comment(lib, "uafxcw.lib")
        #endif
    #endif
#else
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "d.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "d.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER ".lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER ".lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "ud.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "ud.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "u.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "u.lib")
        #endif
    #endif
#endif
```

Archivos de encabezado MFC también incluyen directivas para vincular todas las bibliotecas requeridas, incluidas las bibliotecas MFC, bibliotecas de Win32, las bibliotecas OLE, las bibliotecas OLE creadas a partir de ejemplos, las bibliotecas ODBC y así sucesivamente.

## <a name="ansi-mbcs-and-unicode"></a>ANSI, MBCS y Unicode

Las versiones de la biblioteca de ANSI/MBCS de MFC admiten ambos conjuntos de caracteres de byte único, como ASCII y juegos de caracteres multibyte como Shift-JIS. Las versiones de la biblioteca de Unicode de MFC admiten Unicode en su forma codificada de UTF-16LE caracteres anchos. Use las versiones de la biblioteca de ANSI/MBCS de MFC para la compatibilidad con Unicode había codificado con UTF-8.

Para establecer la configuración del proyecto para usar un solo byte, multibyte o carácter de toda la cadena y carácter de compatibilidad con Unicode en el IDE, utilice el **las propiedades del proyecto** cuadro de diálogo. En el **propiedades de configuración** > **General** , establezca el **del juego de caracteres** propiedad **no establecido** para usar un juego de caracteres de byte único. Establezca la propiedad en **utilizar juego de caracteres multibyte** para usar un juego de caracteres multibyte, o a **utilizar juego de caracteres Unicode** va a utilizar Unicode codificada como UTF-16.

Los proyectos MFC utilizan el símbolo de preprocesador \_UNICODE para indicar la compatibilidad de Unicode de caracteres anchos de UTF-16, y \_compatibilidad con MBCS para indicar MBCS. Estas opciones son mutuamente excluyentes en un proyecto.

## <a name="mfc-static-library-naming-conventions"></a>Convenciones de nomenclatura de biblioteca estática de MFC

Bibliotecas estáticas de MFC utilizan las siguientes convenciones de nomenclatura. Los nombres de biblioteca tienen el formato

> <em>u</em>AFX<em>cd</em>.LIB

donde las letras en cursiva en minúsculas son marcadores de posición para los especificadores, cuyo significado se muestra en la tabla siguiente:

|Especificador|Los valores y significados|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) o Unicode (U); Omitir para la versión sin controles MFC en los cuadros de diálogo|
|*c*|Versión con controles MFC en los cuadros de diálogo (CW) o sin (NMCD)|
|*d*|Depuración o lanzamiento: D. = Debug; omitir el especificador de versión|

Todas las bibliotecas que se muestran en la tabla siguiente se incluyen creado previamente en el directorio \atlmfc\lib para las arquitecturas de compilación admitidos.

|Biblioteca|Descripción|
|-------------|-----------------|
|NAFXCW.LIB|Biblioteca de vínculos estáticos de MFC, versión de lanzamiento|
|NAFXCWD.LIB|Biblioteca de vínculos estáticos de MFC, versión de depuración|
|UAFXCW.LIB|Biblioteca de vínculos estáticos de MFC con compatibilidad con Unicode, versión de lanzamiento|
|UAFXCWD.LIB|Biblioteca de vínculos estáticos de MFC con compatibilidad con Unicode, versión de depuración|
|AFXNMCD.LIB|Biblioteca de vínculos estáticos MFC sin controles de cuadro de diálogo MFC, versión de lanzamiento|
|AFXNMCDD.LIB|Biblioteca de vínculos estáticos MFC sin controles de cuadro de diálogo MFC, versión de depuración|

Los archivos de depurador que tienen el mismo nombre base y una extensión .pdb también están disponibles para cada una de las bibliotecas estáticas.

## <a name="mfc-shared-dll-naming-conventions"></a>Convenciones de nomenclatura de DLL compartidas de MFC

La MFC archivos DLL compartidos también siga una convención de nomenclatura estructurada. Esto facilita la sabe qué archivo DLL o la biblioteca que se debe utilizar con qué propósito.

Los archivos DLL de MFC tienen *versión* números que indican la compatibilidad binaria. Utilizar archivos DLL de MFC que tienen la misma versión que las otras bibliotecas y conjunto de herramientas del compilador para garantizar la compatibilidad dentro de un proyecto.

|Archivo DLL|Descripción|
|---------|-----------------|
|MFC*versión*. ARCHIVO DLL|Versión de DLL de MFC, ANSI o versión MBCS|
|MFC*versión*U.DLL|DLL de MFC, versión de lanzamiento de Unicode|
|MFC*versión*D.DLL|Versión de DLL de MFC, ANSI o MBCS de depuración|
|MFC*version*UD.DLL|DLL de MFC, versión de depuración de Unicode|
|MFCM*versión*. ARCHIVO DLL|DLL de MFC con controles de Windows Forms, versión de MBCS o ANSI|
|MFCM*versión*U.DLL|DLL de MFC con controles de formularios de Windows, versión de lanzamiento de Unicode|
|MFCM*versión*D.DLL|DLL de MFC con controles de Windows Forms, versión ANSI o MBCS de depuración|
|MFCM*versión*UD. ARCHIVO DLL|DLL de MFC con controles de formularios de Windows, versión de depuración de Unicode|

Las bibliotecas de importación necesarias para crear aplicaciones o archivos DLL que usan estos archivos DLL compartidos de extensión MFC tienen el mismo nombre base que el archivo DLL, pero tienen una extensión de nombre de archivo .lib. Al usar los archivos DLL compartidos, una pequeña biblioteca estática todavía debe vincularse con el código; Esta biblioteca se denomina MFCS*versión*.lib {U} {D}.

Si se vincula dinámicamente a la versión compartida del archivo DLL de MFC, ya sea desde una aplicación o desde un archivo DLL de extensión MFC, debe incluir la búsqueda de coincidencias MFC*versión*. Archivo DLL o MFC*versión*U.DLL al implementar el producto.

Para obtener una lista de DLL de Visual C++ que se puede distribuir con sus aplicaciones, consulte [código distribuible para Microsoft Visual Studio 2017 y Microsoft Visual Studio 2017 SDK (incluye utilidades y archivos BuildServer)](http://go.microsoft.com/fwlink/p/?LinkId=823098).

Para obtener más información sobre la compatibilidad con MBCS y Unicode en MFC, vea [juego de caracteres Multibyte (MBCS) compatibilidad con Unicode y](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Compatibilidad con la biblioteca de vínculos dinámicos

Puede usar cualquier static o shared dinámicas bibliotecas MFC para crear archivos DLL que se pueden utilizar los archivos ejecutables MFC y no basados en MFC. Se denominan "archivos DLL estándar" o "archivos DLL estándar MFC" distinguirlos de extensión de MFC archivos DLL que solo se pueden usan las aplicaciones MFC y MFC DLL. Un archivo DLL compilado mediante el uso de las bibliotecas estáticas de MFC a veces se denomina un USRDLL en referencias anteriores, porque los proyectos de DLL de MFC definen el símbolo de preprocesador  **\_USRDLL**. Un archivo DLL que MFC utiliza archivos DLL compartidos a veces se denominaba AFXDLL en referencias anteriores, debido a que define el símbolo de preprocesador  **\_AFXDLL**.

Cuando se crea el proyecto DLL al vincular con las bibliotecas estáticas de MFC, se puede implementar el archivo DLL sin MFC archivos DLL compartidos. Cuando el proyecto DLL está vinculado a las bibliotecas de importación MFC*versión*. LIB o MFC*versión*U.LIB, debe implementar la coincidencia de MFC compartido DLL MFC*versión*. Archivo DLL o MFC*versión*U.DLL junto con el archivo DLL. Para obtener más información, consulte [dll](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)
