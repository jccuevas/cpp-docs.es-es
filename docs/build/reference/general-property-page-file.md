---
title: Página de propiedades General (Archivo)
ms.date: 08/30/2019
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: a9281a0ea02bd9b1fd529453cb9a67e54e4ddda7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168984"
---
# <a name="general-property-page-file"></a>Página de propiedades General (Archivo)

Este tema se aplica a los proyectos de Windows. Para los proyectos que no son de Windows, consulte referencia de la [Página de propiedades de Linux C++ ](../../linux/prop-pages-linux.md).

Al hacer clic con el botón secundario en un nodo de archivo **Explorador de soluciones**, se abre la página de propiedades **General** en el nodo **propiedades de configuración** . Contiene las siguientes propiedades:

- **Excluido de la compilación**

   Especifica si el archivo debe estar en la compilación para la configuración actual.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>.

- **Contenido** (solo se aplica a aplicaciones para UWP). Especifica si el archivo contiene contenido que se incluirá en el paquete de la aplicación.

- **Tipo de elemento**

   El **tipo de elemento** especifica la herramienta que se utilizará para procesar el archivo durante el proceso de compilación. [Los archivos cuya extensión es conocida por Visual Studio](/visualstudio/extensibility/visual-cpp-project-extensibility?view=vs-2019#project-items) tienen un valor predeterminado en esta propiedad. Puede especificar una herramienta personalizada aquí si tiene un tipo de archivo personalizado o desea reemplazar la herramienta predeterminada para un tipo de archivo conocido. Vea [Especificar las herramientas de compilación personalizadas](../specifying-custom-build-tools.md) para obtener más información. También puede usar esta página de propiedades para especificar que un archivo no forma parte del proceso de compilación.

   En la ilustración siguiente se muestra la página de propiedades de un archivo *. cpp* . El **tipo de elemento** predeterminado para este tipo de archivo es el **compilador de C/C++**  (*cl. exe*) y la página de propiedades expone varias configuraciones de compilador que solo se pueden aplicar a este archivo.

   ![Página de propiedades general de un elemento de proyecto](media/file-general-item-type.png "Opciones de tipo de elemento")

    En la tabla siguiente se enumeran los tipos de elemento predeterminados:

    |Extensión de archivo|Tipo de elemento|Herramienta predeterminada|
    |-|-|-|
    |. appx|Definición de la aplicación XAML|[Paquete de aplicaciones](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |. HLSL,. CSO|Compilador de HLSL|[FXC. exe](/windows/win32/direct3dtools/fxc)|
    |.h|Encabezado deC++ C/|[Preprocesador C/C++](../../preprocessor/c-cpp-preprocessor-reference.md)|
    |N/D|No participa en la compilación|N/D|
    |. XML,. XSLT,. xsl|Xml|[Editor XML](/visualstudio/xml-tools/xml-editor)|
    |. resw,. resjson|Recurso PRI (aplicaciones UWP)|[MakePri. exe](/windows/uwp/app-resources/compile-resources-manually-with-makepri)|
    ||Medios (UWP)|[Paquete de aplicaciones](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.xsd|Herramienta Generador de datos XML|[Herramienta de definición de esquemas XML (XSD. exe)](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) (requiere la carga de trabajo de .net. No se incluye con MSVC).|
    ||Herramienta Manifiesto|[MT. exe](/windows/win32/sbscs/mt-exe)|
    |.rc|Resource|[Compilador de recursos de Windows (RC. exe)](/windows/win32/menurc/resource-compiler)|
    |. appxmanifest|Manifiesto del paquete de la aplicación|[Paquete de aplicaciones](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.obj|Object|[C/C++ Linker (link. exe)](cl-invokes-the-linker.md)|
    |. ttf|Fuente|N/D|
    |.txt|Texto|N/D|
    |N/D|Herramienta de compilación personalizada|Definidas por el usuario|
    |N/D|Copiar archivo|N/D|
    |. packagelayout|Diseño del paquete de aplicaciones|[Paquete de aplicaciones](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.resx|Recurso administrado del compilador|[Resgen.exe (generador de archivos de recursos)](/dotnet/framework/tools/resgen-exe-resource-file-generator)|
    |. natvis|C++Archivo de visualización del depurador|[Marco Natvis](/visualstudio/debugger/create-custom-views-of-native-objects)|
    |. jpg,. bmp,. ico, etc.|Imagen|El compilador de recursos basado en el tipo de aplicación.|
    |.cpp|C/C++ compilador|cl. exe|

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>.

Para obtener información sobre cómo obtener acceso a la página de propiedades **General** en el nodo **propiedades de configuración** , vea [establecer C++ las propiedades del compilador y compilación en Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Consulte también

[C++referencia de la página de propiedades del proyecto](property-pages-visual-cpp.md)
