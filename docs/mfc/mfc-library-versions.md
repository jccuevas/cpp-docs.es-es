---
title: Versiones de la biblioteca MFC | Documentos de Microsoft
ms.custom: 
ms.date: 1/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7641a970c747576fa3cfd8cd1c00602edb3541e2
ms.sourcegitcommit: 56f6fce7d80e4f61d45752f4c8512e4ef0453e58
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="mfc-library-versions"></a>Versiones de la biblioteca MFC

La biblioteca MFC está disponible en las versiones compatibles con ANSI de un byte y juego de caracteres multibyte (MBCS) código, así como versiones que admiten Unicode (codificado como UTF-16LE, el juego de caracteres nativo de Windows). Cada versión MFC está disponible como una biblioteca estática o como un archivo DLL compartido. También hay una versión de biblioteca estática MFC más pequeña que deja los controles MFC para los cuadros de diálogo, para las aplicaciones que son muy sensibles a tamaño y no necesitan estos controles. Las bibliotecas MFC están disponibles en ambas versiones de depuración y versión para arquitecturas compatibles que incluyen x86, x64 y procesadores ARM. Puede crear ambas aplicaciones (archivos .exe) y los archivos DLL con cualquier versión de las bibliotecas MFC. Hay también un conjunto de bibliotecas MFC compiladas para interactuar con código administrado. Archivos DLL MFC compartidos incluyen un número de versión para indicar la compatibilidad binaria de la biblioteca.

## <a name="automatic-linking-of-mfc-library-versions"></a>Vinculación automática de versiones de la biblioteca MFC

Los archivos de encabezado MFC determinan automáticamente la versión correcta de la biblioteca MFC para crear un vínculo, en función de los valores definidos en el entorno de compilación. Los archivos de encabezado MFC agregan directivas de compilador que indican al vinculador para vincular en una versión específica de la biblioteca MFC.

Por ejemplo, el archivo AFX. Archivo de encabezado H indica al vinculador que debe vincular la completa estática, limitada estática o compartida versión de DLL de MFC; Versión de ANSI/MBCS o Unicode; y la versión de depuración o minorista, dependiendo de la configuración de compilación:

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

Archivos de encabezado MFC también directivas #include a vincular en todas las bibliotecas requeridas, incluidas las bibliotecas MFC, bibliotecas Win32, bibliotecas OLE, bibliotecas OLE creadas a partir de ejemplos, bibliotecas ODBC y así sucesivamente. 

## <a name="ansi-mbcs-and-unicode"></a>ANSI, MBCS y Unicode

Las versiones de la biblioteca de ANSI/MBCS para MFC admiten ambos conjuntos de caracteres de un solo byte, como ASCII y juegos de caracteres multibyte como Shift-JIS. Las versiones de la biblioteca MFC Unicode admiten Unicode en su forma codificada en UTF-16LE con caracteres anchos. Utilice las versiones de la biblioteca de ANSI/MBCS de MFC para la compatibilidad con Unicode con codificación UTF-8.

Para establecer la configuración del proyecto para usar un solo byte, multibyte o carácter de toda la cadena y carácter compatibilidad con Unicode en el IDE, utilice el **propiedades del proyecto** cuadro de diálogo. En el **propiedades de configuración** > **General** , establezca el **del juego de caracteres** propiedad **no establece** para usar un juego de caracteres de un solo byte. Establezca la propiedad en **utilizar juego de caracteres multibyte** para usar un juego de caracteres multibyte, o a **utilizar juego de caracteres Unicode** para utilizar Unicode codificada como UTF-16.

Proyectos MFC utilizan el símbolo de preprocesador  **\_UNICODE** para indicar la compatibilidad de Unicode de caracteres anchos de UTF-16, y  **\_MBCS** para indicar la compatibilidad con MBCS. Estas opciones son mutuamente excluyentes en un proyecto.

## <a name="mfc-static-library-naming-conventions"></a>Convenciones de nomenclatura de biblioteca estática de MFC

Bibliotecas estáticas de MFC utilizan las siguientes convenciones de nomenclaturas. Los nombres de biblioteca tienen el formato

> *u*AFX*c ** d.*. LIB

donde las letras en cursiva en minúsculas son marcadores de posición para los especificadores, cuyos significados se muestran en la tabla siguiente:

|Especificador|Valores y significados|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) o Unicode (U); Omitir para la versión sin controles MFC en los cuadros de diálogo|
|*c*|Versión con controles MFC en los cuadros de diálogo (CW) o sin (NMCD)|
|*d*|Depuración o lanzamiento: D. = Debug; omitir el especificador de versión|

Todas las bibliotecas de aparecen en la tabla siguiente se incluyen creada previamente en el directorio \atlmfc\lib para crear arquitecturas de versión compatible.

|Biblioteca|Descripción|
|-------------|-----------------|
|NAFXCW.LIB|Biblioteca de vínculos estáticos de MFC, versión de lanzamiento|
|NAFXCWD.LIB|Biblioteca de vínculos estáticos de MFC, versión de depuración|
|UAFXCW.LIB|Biblioteca de vínculos estáticos de MFC con compatibilidad con Unicode, versión de lanzamiento|
|UAFXCWD.LIB|Biblioteca de vínculos estáticos de MFC con compatibilidad con Unicode, versión de depuración|
|AFXNMCD. LIB|Biblioteca de vínculos estáticos de MFC sin controles de cuadro de diálogo MFC, versión de lanzamiento|
|AFXNMCDD. LIB|Biblioteca de vínculos estáticos de MFC sin controles de cuadro de diálogo MFC, versión de depuración|

Archivos de depurador que tienen el mismo nombre base y una extensión de archivo .pdb también están disponibles para cada una de las bibliotecas estáticas.

## <a name="mfc-shared-dll-naming-conventions"></a>Convenciones de nomenclatura de DLL compartidas de MFC

La MFC compartidos dll también siguen una convención de nomenclatura estructurada. Esto hace más fácil saber qué archivo DLL o la biblioteca debe utilizar para cada propósito.

Los archivos DLL de MFC tienen *versión* números que indican la compatibilidad binaria. Utilizar archivos DLL de MFC que tengan la misma versión que las otras bibliotecas y conjunto de herramientas de compilador para garantizar la compatibilidad dentro de un proyecto.

|Archivo DLL|Descripción|
|---------|-----------------|
|MFC*versión*. ARCHIVO DLL|Versión de DLL de MFC, ANSI o versión MBCS|
|MFC*versión*U.DLL|DLL de MFC, versión de lanzamiento de Unicode|
|MFC*versión*D.DLL|Versión de DLL de MFC, ANSI o MBCS de depuración|
|MFC*versión*UD. ARCHIVO DLL|DLL de MFC, versión de depuración Unicode|
|MFCM*versión*. ARCHIVO DLL|DLL de MFC con controles de formularios Windows Forms, versión ANSI o versión MBCS|
|MFCM*versión*U.DLL|DLL de MFC con controles de formularios Windows Forms, versión de lanzamiento de Unicode|
|MFCM*versión*D.DLL|DLL de MFC con controles de formularios Windows Forms, versión ANSI o MBCS de depuración|
|MFCM*versión*UD. ARCHIVO DLL|DLL de MFC con controles de formularios Windows Forms, versión de depuración Unicode|

Las bibliotecas de importación necesarias para generar aplicaciones o archivos DLL que utilicen estos archivos DLL compartidas de extensión de MFC tienen el mismo nombre base que el archivo DLL, pero tienen una extensión de nombre de archivo .lib. Cuando usa los archivos DLL compartidos, una biblioteca estática pequeña todavía debe estar vinculada al código; Esta biblioteca se denomina MFCS*versión*.lib {U} {D}.

Si se vincula dinámicamente a la versión compartida del archivo DLL de MFC, ya sea desde una aplicación o desde un archivo DLL de extensión MFC, se debe incluir la búsqueda de coincidencias MFC*versión*. Archivo DLL o MFC*versión*U.DLL al implementar el producto.

Para obtener una lista de archivos DLL de C++ Visual que se puede distribuir con las aplicaciones, consulte [código distribuible para Microsoft Visual Studio 2017 y Microsoft Visual Studio 2017 SDK (incluye utilidades y archivos BuildServer)](http://go.microsoft.com/fwlink/p/?LinkId=823098).

Para obtener más información sobre la compatibilidad con MBCS y Unicode en MFC, vea [con los juegos de caracteres Multibyte (MBCS) compatibilidad con Unicode y](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Compatibilidad con bibliotecas de vínculos dinámicos

Puede usar cualquier estáticas o compartidas dinámicas bibliotecas MFC para crear archivos DLL que pueden utilizarse en archivos ejecutables de MFC y no basada en MFC. Se denominan "archivos DLL estándar" o "DLL MFC estándar" distinguirlos de extensión de MFC archivos DLL que solo puede ser utilizan por aplicaciones MFC y MFC DLL. Un archivo DLL compilado mediante el uso de las bibliotecas estáticas de MFC se denomina un USRDLL en las referencias anteriores, porque los proyectos de DLL de MFC definen el símbolo de preprocesador  **\_USRDLL**. Un archivo DLL que utiliza la MFC archivos DLL compartidos se denomina AFXDLL en las referencias anteriores, ya que define el símbolo de preprocesador  **\_AFXDLL**.

Cuando crea el proyecto DLL al vincular a bibliotecas estáticas MFC, se puede implementar el archivo DLL sin la MFC archivos DLL compartidos. Cuando el proyecto DLL está vinculado a las bibliotecas de importación MFC*versión*. LIB o MFC*versión*U.LIB, debe implementar la coincidencia de MFC compartido DLL MFC*versión*. Archivo DLL o MFC*versión*U.DLL junto con el archivo DLL. Para obtener más información, consulte [dll](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)  
