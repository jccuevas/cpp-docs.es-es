---
title: Consumo de bibliotecas y componentes en proyectos de C++
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: c7facb82054eed4ef28c52830b8a3079eecb7fdc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169960"
---
# <a name="consuming-libraries-and-components"></a>Consumo de bibliotecas y componentes

A menudo, un proyecto de C++ necesita llamar a funciones o tener acceso a los datos de un archivo binario, como una biblioteca estática (archivos .lib), un archivo DLL, un componente de Windows Runtime, un componente COM o un ensamblado de .NET. En estos casos, tiene que configurar el proyecto para que pueda encontrar ese archivo binario en tiempo de compilación. Los pasos específicos dependen del tipo de proyecto, del tipo de archivo binario y de si el binario se va a compilar en la misma solución que el proyecto.

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>Consumo de bibliotecas descargadas a través de vcpkg

Para consumir una biblioteca que se ha descargado mediante el administrador de paquetes **vcpkg**, puede omitir las instrucciones siguientes. Consulte [vcpkg: un administrador de paquetes de C++ para Windows, Linux y MacOS](vcpkg.md#integrate-with-visual-studio-windows) para obtener más información.

## <a name="consuming-static-libraries"></a>Consumo de bibliotecas estáticas

Si el proyecto de biblioteca estática se va a compilar en la misma solución:

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>Incluya los archivos de encabezado de la biblioteca estática entre comillas. En una solución típica, la ruta de acceso se iniciará con `../<library project name>`. IntelliSense le ayudará a encontrarla.
2. Agregue una referencia al proyecto de biblioteca estática. Haga clic con el botón derecho en **Referencias** en el nodo del proyecto de prueba en el **Explorador de soluciones** y elija **Agregar referencia**.

Si la biblioteca estática no forma parte de la solución:

1. Haga clic con el botón derecho en el nodo del proyecto de aplicación en el **Explorador de soluciones** y elija **Propiedades**.
2. En la página de propiedades **Directorios de VC++** , agregue la ruta de acceso al directorio donde se encuentra el archivo .lib en **Rutas de acceso de biblioteca** y agregue la ruta de acceso a los archivos de encabezado de la biblioteca en **Directorios de archivos de inclusión**.  
3. En la página de propiedades **Enlazador > Entrada**, agregue el nombre del archivo .lib a **Dependencias adicionales**.

## <a name="dynamic-link-libraries"></a>Bibliotecas de vínculos dinámicos

Si el archivo DLL se va a compilar como parte de la misma solución que la aplicación, siga los mismos pasos que para una biblioteca estática.

Si el archivo DLL no forma parte de la solución de aplicación, necesita el archivo DLL, los encabezados con prototipos para las funciones y las clases exportadas, y un archivo .lib que proporciona la información de vinculación necesaria.

1. Copie el archivo DLL en la carpeta de salida del proyecto o en otra carpeta de la ruta de búsqueda estándar de Windows para archivos DLL. Consulte [Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/win32/dlls/dynamic-link-library-search-order).
2. Siga los pasos 1-3 para que las bibliotecas estáticas proporcionen las rutas de acceso a los encabezados y al archivo .lib.

## <a name="com-objects"></a>objetos COM

Si la aplicación nativa de C++ necesita consumir un objeto COM y ese objeto está *registrado*, lo único que debe hacer es llamar a CoCreateInstance y pasar el CLSID del objeto. El sistema lo encontrará en el Registro de Windows y lo cargará. Un proyecto de C++/CLI puede consumir un objeto COM de la misma manera, o bien puede agregar una referencia a él desde la lista **Agregar referencias > COM** y consumirlo a través de su [contenedor RCW](/dotnet/framework/interop/runtime-callable-wrapper).

## <a name="net-assemblies-and-windows-runtime-components"></a>Ensamblados de .NET y componentes de Windows Runtime

En los proyectos de UWP o de C++/CLI, se consumen ensamblados de .NET o componentes de Windows Runtime agregando una *referencia* a ellos. En el nodo **Referencias** de un proyecto de UWP o de C++/CLI, verá referencias a los componentes más usados. Haga clic con el botón derecho en el nodo **Referencias** en el **Explorador de soluciones** para abrir el **Administrador de referencias** y examinar los componentes adicionales que el sistema conoce. Haga clic en el botón **Examinar** para ir a cualquier carpeta en la que se encuentre un componente personalizado. Dado que los ensamblados de .NET y los componentes de Windows Runtime contienen información de tipos integrados, puede ver sus métodos y clases haciendo clic con el botón derecho y eligiendo la opción **Ver en el Examinador de objetos**.

## <a name="reference-properties"></a>Propiedades de referencia

Cada tipo de referencia tiene propiedades. Para ver las propiedades, seleccione la referencia en el Explorador de soluciones y presione **Alt + Entrar**, o bien haga clic con el botón derecho y elija **Propiedades**. Algunas propiedades son de solo lectura y algunas pueden modificarse. Sin embargo, normalmente estas propiedades no deben modificarse de forma manual.

### <a name="activex-reference-properties"></a>Propiedades de referencias de ActiveX

Las propiedades de referencias de ActiveX solo están disponibles para las referencias a componentes COM. Estas propiedades solo se muestran cuando se selecciona un componente COM en el panel **Referencias** . No se pueden modificar las propiedades.

- **Ruta de acceso de control**

   Muestra la ruta de acceso del directorio del control al que se hace referencia.

- **GUID de control**

   Muestra el GUID del control ActiveX.

- **Versión de control**

   Muestra la versión del control ActiveX al que se hace referencia.

- **Nombre de biblioteca de tipos**

   Muestra el nombre de la biblioteca de tipos a la que se hace referencia.

- **Herramienta de contenedor**

   Muestra la herramienta que se utiliza para compilar el ensamblado de interoperabilidad desde el control ActiveX o la biblioteca COM a los que se hace referencia.

### <a name="assembly-reference-properties-ccli"></a>Propiedades de referencias de ensamblados (C++/CLI)

Las propiedades de referencias de ensamblados solo están disponibles para referencias a ensamblados de .NET Framework en proyectos de C++/CLI. Estas propiedades solo se muestran cuando se selecciona un ensamblado de .NET Framework en el panel **Referencias**. No se pueden modificar las propiedades.

- **Ruta relativa**

   Muestra la ruta de acceso relativa desde el directorio del proyecto hasta el ensamblado al que se hace referencia.

### <a name="build-properties"></a>Propiedades de compilación

Las propiedades siguientes están disponibles en diversos tipos de referencia. Estas propiedades permiten especificar cómo compilar con referencias.

- **Copia local**

   Especifica si se debe copiar automáticamente el ensamblado al que se hace referencia en la ubicación de destino durante una compilación.

- **Copia local de ensamblados satélite (C++/CLI)**

   Especifica si se deben copiar automáticamente los ensamblados satélite del ensamblado al que se hace referencia en la ubicación de destino durante una compilación. Solo se utiliza si el valor de **Copia local** es **true**.

- **Salida de ensamblado de referencia**

   Especifica que este ensamblado se usa en el proceso de compilación. Si el valor es **true**, el ensamblado se agregará a la línea de comandos del compilador durante la compilación.

### <a name="project-to-project-reference-properties"></a>Propiedades de referencia de proyecto a proyecto

Las siguientes propiedades definen una *referencia de proyecto a proyecto* del proyecto que está seleccionado en el panel **Referencias** a otro proyecto en la misma solución. Para más información, vea [Administrar referencias en un proyecto](/visualstudio/ide/managing-references-in-a-project).

- **Dependencias de la biblioteca de vínculos**

   Cuando esta propiedad es **True**, el sistema de proyectos vincula dentro del proyecto dependiente los archivos .lib generados por el proyecto independiente. Por lo general, usted especificará **True**.

- **Identificador del proyecto**

   Identifica de forma única el proyecto independiente. El valor de propiedad es un GUID de sistema interno que no se puede modificar.

- **Usar entradas de dependencia de biblioteca**

   Cuando esta propiedad es **False**, el sistema de proyectos no vincula dentro del proyecto dependiente los archivos .obj de la biblioteca generada por el proyecto independiente. Por lo tanto, este valor deshabilita la vinculación incremental. Normalmente especificará **False** , porque compilar la aplicación puede tardar mucho tiempo si hay muchos proyectos independientes.

### <a name="read-only-reference-properties-com--net"></a>Propiedades de referencias de solo lectura (COM y .NET)

Las siguientes propiedades se encuentran en las referencias de ensamblado de .NET y COM y no se puede modificar.

- **Nombre del ensamblado**

   Muestra el nombre del ensamblado al que se hace referencia.

- **Referencia cultural**

   Muestra la referencia cultural de la referencia seleccionada.

- **Descripción**

   Muestra la descripción de la referencia seleccionada.

- **Ruta de acceso completa**

   Muestra la ruta de acceso del directorio del ensamblado al que se hace referencia.

- **Identity**

   Para los ensamblados de .NET Framework, muestra la ruta de acceso completa. Para los componentes COM, muestra el GUID.

- **Label**

   Muestra la etiqueta de la referencia.

- **Nombre**

   Muestra el nombre de la referencia.

- **Token de clave pública**

   Muestra el token de clave pública que se utiliza para identificar el ensamblado al que se hace referencia.

- **Nombre seguro**

   `true` si el ensamblado al que se hace referencia tiene un nombre seguro. Un ensamblado con nombre seguro tiene una única versión.

- **Versión**

   Muestra la versión del ensamblado al que se hace referencia.

## <a name="see-also"></a>Vea también

[Referencia de las páginas de propiedades de un proyecto de C++](reference/property-pages-visual-cpp.md)<br>
[Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](working-with-project-properties.md)
