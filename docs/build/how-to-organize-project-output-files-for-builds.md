---
title: Filtrar Organizar archivos de salida del proyecto para compilaciones
ms.date: 11/04/2016
helpviewer_keywords:
- Visual C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
ms.openlocfilehash: a675b535577b8757e92246249c94cd9760534740
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827094"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>Procedimiento Organizar archivos de salida del proyecto para compilaciones

En este tema se describen los procedimientos recomendados para organizar los archivos de salida del proyecto. Los errores de compilación se pueden producir al configurar los archivos de salida del proyecto de forma incorrecta. En este tema también se describen las ventajas y desventajas de cada alternativa para organizar los archivos de salida del proyecto.

## <a name="referencing-clr-assemblies"></a>Hacer referencia a ensamblados CLR

#### <a name="to-reference-assemblies-with-using"></a>Para hacer referencia a los ensamblados con #using

1. Se puede hacer referencia a un ensamblado directamente desde el código mediante la directiva #using, como `#using <System.Data.dll>`. Para obtener más información, vea [#using (directiva)](../preprocessor/hash-using-directive-cpp.md).

   El archivo especificado puede ser un archivo .dll, .exe, .netmodule o .obj, siempre y cuando esté en MSIL. El componente al que se hace referencia se puede compilar en cualquier lenguaje. Con esta opción, tendrá acceso a IntelliSense ya que los metadatos se van a extraer desde MSIL. El archivo en cuestión debe estar en la ruta de acceso del proyecto; en caso contrario, el proyecto no se compilará e IntelliSense no estará disponible. Una manera fácil de determinar si el archivo está en la ruta de acceso consiste en hacer clic con el botón derecho en la línea #using y seleccionar el comando **Abrir documento**. Se le notificará si no se puede encontrar el archivo.

   Si no quiere colocar la ruta de acceso completa al archivo, puede usar la opción del compilador **/AI** para editar la ruta de acceso de búsqueda para las referencias #using. Para obtener más información, consulte [/AI (Especificar directorios de metadatos)](reference/ai-specify-metadata-directories.md).

#### <a name="to-reference-assemblies-with-fu"></a>Para hacer referencia a los ensamblados con /FU

1. En lugar de hacer referencia a un ensamblado directamente desde un archivo de código, como se ha descrito anteriormente, se puede usar la opción del compilador **/FU**. La ventaja de este método es que no es necesario agregar una instrucción #using a todos los archivos que hacen referencia a un ensamblado dado.

   Para establecer esta opción, abra la **Páginas de propiedades** del proyecto. Expanda el nodo **Propiedades de configuración** y, después, expanda el nodo **C/C++** y haga clic en **Avanzado**. Agregue los ensamblados deseados junto a **Forzar #using**. Para obtener más información, consulte [/FU (Dar nombre al archivo #using forzado)](reference/fu-name-forced-hash-using-file.md).

#### <a name="to-reference-assemblies-with-add-new-reference"></a>Para hacer referencia a los ensamblados con Agregar nueva referencia

1. Se trata de la manera más sencilla de usar los ensamblados CLR. En primer lugar, asegúrese de que el proyecto se compila con la opción del compilador **/clr**. Después, haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Agregar**, **Referencias**. Se abrirá el cuadro de diálogo **Páginas de propiedades**.

1. Desde el cuadro de diálogo **Páginas de propiedades**, haga clic en **Agregar nueva referencia**. Aparecerá un cuadro de diálogo en el que se enumeran todos los ensamblados .NET, COM y de otros tipos disponibles en el proyecto actual. Seleccione el ensamblado deseado y haga clic en **Aceptar**.

   Una vez que se establece una referencia de proyecto, las dependencias correspondientes se administran de manera automática. Además, como los metadatos forman parte de un ensamblado, no es necesario agregar un archivo de encabezado o prototipo a los elementos que se usan desde los ensamblados administrados.

## <a name="referencing-native-dlls-or-static-libraries"></a>Hacer referencia a archivos DLL nativos o bibliotecas estáticas

#### <a name="to-reference-native-dlls-or-static-libraries"></a>Para hacer referencia a archivos DLL nativos o bibliotecas estáticas

1. Haga referencia al archivo de encabezado adecuado en el código mediante la directiva #include. El archivo de encabezado debe estar en la ruta de acceso de inclusión o formar parte del proyecto actual. Para obtener más información, vea [#include (directiva) (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).

1. También puede establecer dependencias del proyecto. Al establecer las dependencias del proyecto se garantizan dos cosas. En primer lugar, se asegura de que los proyectos se compilen en el orden correcto para que un proyecto siempre pueda encontrar los archivos dependientes que necesita. En segundo lugar, se agrega implícitamente el directorio de salida del proyecto dependiente a la ruta de acceso para que los archivos se puedan encontrar fácilmente en tiempo de vinculación.

1. Para implementar la aplicación, debe colocar el archivo DLL en un lugar adecuado. Este puede ser uno de los siguientes:

   1. La misma ruta de acceso del archivo ejecutable.

   1. En cualquier parte de la ruta de acceso del sistema (la variable de entorno **path**).

   1. En el ensamblado en paralelo. Para obtener más información, vea [Compilar ensamblados simultáneos de C/C++](building-c-cpp-side-by-side-assemblies.md).

## <a name="working-with-multiple-projects"></a>Trabajar con varios proyectos

De forma predeterminada, los proyectos se compilan de forma que todos los archivos de salida se crean en un subdirectorio del directorio del proyecto. El directorio se denomina en función de la configuración de compilación (por ejemplo, Debug o Release). Para que los proyectos del mismo nivel se hagan referencia entre sí, cada proyecto debe agregar explícitamente los directorios de salida del otro a su ruta de acceso para que la vinculación sea correcta. Esto se realiza de manea automática al establecer las dependencias del proyecto. Pero si no se usan dependencias, esto se debe controlar cuidadosamente porque las compilaciones pueden ser muy difíciles de administrar. Por ejemplo, cuando un proyecto tiene configuraciones de Debug y Release, e incluye una biblioteca externa de un proyecto del mismo nivel, debe usar otro archivo de biblioteca en función de la configuración que se va a compilar. Por tanto, codificar de forma rígida estas rutas de acceso puede ser complicado.

Todos los archivos de salida esenciales (por ejemplo, los archivos ejecutables, de vinculador incrementales y PDB) se copian en un directorio común de la solución. Por tanto, cuando se trabaja con una solución que contiene un número de proyectos de C++ con configuraciones equivalentes, todos los archivos de salida se centralizan para simplificar la vinculación y la implementación. Puede estar seguro de que las aplicaciones y bibliotecas funcionarán según lo esperado si mantiene juntos esos archivos (ya que se garantiza que estarán en la ruta de acceso).

La ubicación de los archivos de salida puede ser un problema importante cuando se implementa en un entorno de producción. Durante la ejecución de proyectos en el IDE, las rutas de acceso a las bibliotecas incluidas no son necesariamente las mismas que en el entorno de producción. Por ejemplo, si tiene `#using "../../lib/debug/mylib.dll"` en el código pero después implementa mylib.dll en otra posición relativa, se producirá un error de la aplicación en tiempo de ejecución. Para evitarlo, debe evitar el uso de rutas de acceso relativas en las instrucciones #include en el código. Es recomendable asegurarse de que los archivos necesarios se encuentran en la ruta de acceso de compilación del proyecto y, del mismo modo, de que los archivos de producción correspondientes están colocados de manera correcta.

#### <a name="how-to-specify-where-output-files-go"></a>Cómo especificar dónde colocar los archivos de salida

1. La ubicación de la configuración de salida del proyecto se puede encontrar en las **Páginas de propiedades** del proyecto. Expanda el nodo situado junto a **Propiedades de configuración** y seleccione **General**. La ubicación de salida se especifica junto a **Directorio de salida**. Para obtener más información, vea [Página de propiedades General (Proyecto)](reference/general-property-page-project.md).

## <a name="see-also"></a>Vea también

[Tipos de proyecto de Visual C++](reference/visual-cpp-project-types.md)
