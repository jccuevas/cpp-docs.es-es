---
title: Versiones de la biblioteca MFC
ms.date: 05/08/2019
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
ms.openlocfilehash: b8e32366d9ff43bd6e5770f64f0ba9d8bf6e56ab
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425704"
---
# <a name="mfc-library-versions"></a>Versiones de la biblioteca MFC

La biblioteca MFC está disponible en las versiones que admiten código ANSI de un solo byte y de juego de caracteres multibyte (MBCS), así como las versiones compatibles con Unicode (codificado como UTF-16LE, el juego de caracteres nativo de Windows). Cada versión de MFC está disponible como biblioteca estática o como DLL compartida. También hay una versión más pequeña de la biblioteca estática de MFC que deja los controles MFC para los cuadros de diálogo, para las aplicaciones que son muy sensibles al tamaño y no necesitan esos controles. Las bibliotecas MFC están disponibles en las versiones de depuración y lanzamiento para las arquitecturas admitidas que incluyen procesadores x86, x64 y ARM. Puede crear aplicaciones (archivos. exe) y dll con cualquier versión de las bibliotecas MFC. También hay un conjunto de bibliotecas MFC compiladas para interactuar con código administrado. Los archivos dll compartidos de MFC incluyen un número de versión para indicar la compatibilidad binaria de la biblioteca.

## <a name="automatic-linking-of-mfc-library-versions"></a>Vinculación automática de las versiones de la biblioteca MFC

Los archivos de encabezado de MFC determinan automáticamente la versión correcta de la biblioteca MFC que se va a vincular, en función de los valores definidos en el entorno de compilación. Los archivos de encabezado de MFC agregan directivas de compilador que indican al enlazador que se vincule en una versión específica de la biblioteca MFC.

Por ejemplo, AFX. El archivo de encabezado H indica al enlazador que vincule en la versión completa de MFC estática, estática limitada o compartida de MFC; ANSI/MBCS o versión Unicode; y la versión de depuración o comercial, en función de la configuración de compilación:

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

Los archivos de encabezado de MFC también incluyen directivas para vincular en todas las bibliotecas requeridas, incluidas las bibliotecas MFC, las bibliotecas Win32, las bibliotecas OLE, las bibliotecas OLE creadas a partir de ejemplos, bibliotecas ODBC, etc.

## <a name="ansi-mbcs-and-unicode"></a>ANSI, MBCS y Unicode

Las versiones de la biblioteca ANSI/MBCS de MFC admiten juegos de caracteres de un solo byte, como ASCII, y juegos de caracteres multibyte como Shift-JIS. Las versiones de la biblioteca Unicode de MFC admiten Unicode en su forma codificada de caracteres anchos UTF-16LE. Use las versiones de la biblioteca ANSI/MBCS de MFC para la compatibilidad con Unicode con codificación UTF-8.

Use el cuadro de diálogo **propiedades del proyecto** para establecer la configuración del proyecto para que use la compatibilidad de caracteres y cadenas Unicode de un solo byte, multibyte o caracteres anchos en el IDE. En la **página Propiedades de configuración** > **General** , establezca la propiedad **juego de caracteres** en **no establecido** en usar un juego de caracteres de un solo byte. Establezca la propiedad en usar juego de caracteres de **varios bytes** para usar un juego de caracteres multibyte, o para usar el juego de caracteres **Unicode** para usar la codificación Unicode como UTF-16.

Los proyectos MFC usan el símbolo de preprocesador \_Unicode para indicar la compatibilidad con Unicode de caracteres anchos UTF-16 y \_MBCS para indicar la compatibilidad con MBCS. Estas opciones se excluyen mutuamente en un proyecto.

## <a name="mfc-static-library-naming-conventions"></a>Convenciones de nomenclatura de la biblioteca estática MFC

Las bibliotecas estáticas para MFC utilizan las siguientes convenciones de nomenclatura. Los nombres de biblioteca tienen el formato

> <em>u</em> <em>CD</em>AFX. OBJ

donde las letras que se muestran en cursiva en cursiva son marcadores de posición para los especificadores cuyos significados se muestran en la tabla siguiente:

|Especificador|Valores y significados|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) o Unicode (U); omitir para la versión sin controles MFC en cuadros de diálogo|
|*c*|Versión con controles MFC en cuadros de diálogo (CW) o sin (NMCD)|
|*d*|Debug o Release: D = Debug; omitir el especificador para la versión|

Todas las bibliotecas enumeradas en la tabla siguiente se incluyen prediseñadas en el directorio \atlmfc\lib para las arquitecturas de compilación compatibles.

|Biblioteca|Descripción|
|-------------|-----------------|
|NAFXCW.LIB|Biblioteca de vínculos estáticos de MFC, versión de lanzamiento|
|NAFXCWD.LIB|Biblioteca de vínculos estáticos de MFC, versión de depuración|
|UAFXCW.LIB|Biblioteca de vínculos estáticos de MFC con compatibilidad con Unicode, versión de lanzamiento|
|UAFXCWD.LIB|Biblioteca de vínculos estáticos de MFC con compatibilidad con Unicode, versión de depuración|
|AFXNMCD.LIB|Biblioteca de vínculos estáticos de MFC sin controles de cuadro de diálogo de MFC, versión de lanzamiento|
|AFXNMCDD.LIB|Biblioteca de vínculos estáticos de MFC sin controles de cuadro de diálogo de MFC, versión de depuración|

Los archivos del depurador que tienen el mismo nombre base y una extensión. pdb también están disponibles para cada una de las bibliotecas estáticas.

## <a name="mfc-shared-dll-naming-conventions"></a>Convenciones de nomenclatura de archivos DLL compartidos de MFC

Los archivos dll compartidos de MFC también siguen una Convención de nomenclatura estructurada. Esto hace más fácil saber qué DLL o biblioteca debe utilizar para cada propósito.

Los archivos dll de MFC tienen números de *versión* que indican compatibilidad binaria. Use archivos dll de MFC que tengan la misma versión que las demás bibliotecas y conjunto de herramientas del compilador para garantizar la compatibilidad dentro de un proyecto.

|DLL|Descripción|
|---------|-----------------|
|*Versión*de MFC. DLL|DLL de MFC, versión de lanzamiento ANSI o MBCS|
|*Versión*de MFC U. dll|Archivo DLL de MFC, versión de lanzamiento Unicode|
|*Versión*D. dll de MFC|DLL de MFC, versión de depuración ANSI o MBCS|
|*Versión*de MFC Ud. DLL|DLL de MFC, versión de depuración Unicode|
|*Versión*de MFCM. DLL|DLL de MFC con controles de Windows Forms, versión de lanzamiento ANSI o MBCS|
|MFCM*versión*U. dll|DLL de MFC con controles de Windows Forms, versión de lanzamiento Unicode|
|MFCM*versión*D. dll|DLL de MFC con controles de Windows Forms, versión de depuración ANSI o MBCS|
|MFCM*versión*Ud. DLL|DLL de MFC con controles de Windows Forms, versión de depuración Unicode|

Las bibliotecas de importación necesarias para compilar aplicaciones o archivos dll de extensión de MFC que usen estos archivos dll compartidos tienen el mismo nombre base que el archivo DLL, pero tienen la extensión de nombre de archivo. lib. Al usar los archivos dll compartidos, una pequeña biblioteca estática debe estar vinculada a su código. Esta biblioteca se denomina MFCS*versión*{U} {D}. lib.

Si está vinculando dinámicamente a la versión de DLL compartida de MFC, tanto si se trata de una aplicación como de un archivo DLL de extensión de MFC, debe incluir la*versión*de MFC correspondiente. DLL o la*versión*de MFC u. dll al implementar el producto.

Para obtener una lista de C++ archivos dll de visual que se pueden distribuir con las aplicaciones, vea [código distribuible para Microsoft Visual Studio 2017 y Microsoft Visual Studio 2017 SDK (incluye utilidades y archivos BuildServer)](/visualstudio/productinfo/2017-redistribution-vs) o [código distribuible para Visual Studio 2019](/visualstudio/releases/2019/redistribution).

Para obtener más información sobre la compatibilidad con MBCS y Unicode en MFC, vea [compatibilidad con Unicode y con el juego de caracteres multibyte (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Compatibilidad con la biblioteca de vínculos dinámicos

Puede usar las bibliotecas MFC estáticas o compartidas de MFC para crear archivos DLL que se pueden usar tanto en archivos ejecutables de MFC como no basados en MFC. Se denominan "archivos DLL estándar" o "archivos dll de MFC normales" para distinguirlos de los archivos dll de extensión de MFC que solo pueden usar las aplicaciones MFC y los archivos dll de MFC. Un archivo DLL compilado con las bibliotecas estáticas de MFC a veces se denomina USRDLL en referencias anteriores, ya que los proyectos de archivos DLL de MFC definen el símbolo del preprocesador **\_USRDLL**. Un archivo DLL que usa los archivos dll compartidos de MFC a veces se denomina AFXDLL en referencias anteriores, ya que define el símbolo del preprocesador **\_AFXDLL**.

Al crear el proyecto DLL vinculando a las bibliotecas estáticas de MFC, el archivo DLL se puede implementar sin los archivos dll compartidos de MFC. Cuando el proyecto DLL se vincula a la*versión*de MFC de las bibliotecas de importación. LIB o la*versión*de MFC u. lib, debe implementar la*versión*MFC del archivo dll compartida MFC correspondiente. DLL o la*versión*de MFC u. dll junto con el archivo dll. Para obtener más información, vea [archivos dll](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Consulte también

[Temas generales de MFC](../mfc/general-mfc-topics.md)
