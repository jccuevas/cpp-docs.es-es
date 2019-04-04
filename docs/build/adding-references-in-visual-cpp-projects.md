---
title: Consumo de bibliotecas y componentes en proyectos de C++
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: eb4d970527ba919af10eadab7c907f5108767b9b
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780475"
---
# <a name="consuming-libraries-and-components"></a>Consumo de bibliotecas y componentes

A menudo, un proyecto de C++ debe llamar a funciones o tener acceso a datos en un archivo binario como biblioteca estática (.lib archivos), DLL, componente de tiempo de ejecución de Windows, el componente de COM o ensamblado. NET. En estos casos, tendrá que configurar el proyecto para que puedan encontrar ese binario en tiempo de compilación. Los pasos específicos dependen del tipo de su proyecto, el tipo del archivo binario, y si se está generando el archivo binario en la misma solución que el proyecto. 

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>Consumo de bibliotecas descargados a través de vcpkg

Para consumir una biblioteca que ha descargado mediante el uso de la **vcpkg** Administrador de paquetes, puede omitir las instrucciones siguientes. Consulte [vcpkg: Un administrador de paquetes de C++ para Windows, Linux y MacOS](vcpkg.md#integrate-with-visual-studio-windows) para obtener más información.

## <a name="consuming-static-libraries"></a>Consumo de bibliotecas estáticas

Si se compila el proyecto de biblioteca estática en la misma solución:

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>incluir los archivos de encabezado para la biblioteca estática con comillas. En una solución típica de la ruta de acceso se iniciará con `../<library project name>`. IntelliSense le ayudará a encontrarlo.
2. Agregue una referencia al proyecto de biblioteca estática. Haga doble clic en **referencias** bajo el nodo de proyecto de aplicación en **el Explorador de soluciones** y elija **Agregar referencia**. 

Si la biblioteca estática no forma parte de la solución:

1. Haga doble clic en el nodo de proyecto de aplicación en **el Explorador de soluciones** y, a continuación, elija **propiedades**. 
2. En el **directorios de VC ++** propiedad página, agregue la ruta de acceso al directorio donde se encuentra el archivo .lib en **las rutas de acceso de la biblioteca** y agregue la ruta de acceso a los archivos de encabezado de la biblioteca de **directorios de inclusión** .  
3. En el **vinculador > entrada** propiedad página, agregue el nombre del archivo .lib para **dependencias adicionales**.

## <a name="dynamic-link-libraries"></a>Bibliotecas de vínculos dinámicos

Si el archivo DLL se compila como parte de la misma solución que la aplicación, siga los mismos pasos que para una biblioteca estática.

Si el archivo DLL no forma parte de la solución de aplicación, necesita el archivo DLL, los encabezados con los prototipos para las funciones exportadas y clases y un archivo .lib que proporciona la información necesaria de vinculación.

1. Copie el archivo DLL en la carpeta de salida del proyecto, o a otra carpeta en la ruta de acceso de búsqueda estándar de Windows para las DLL. Consulte [orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/desktop/dlls/dynamic-link-library-search-order).
2. Siga los pasos 1 a 3 para bibliotecas estáticas proporcionar las rutas de acceso a los encabezados y el archivo .lib.

## <a name="com-objects"></a>objetos COM

Si su aplicación C++ nativa necesita consumir un objeto COM, y ese objeto es *registrado*, a continuación, lo único que debe hacer es llamar a CoCreateInstance y pasar el CLSID del objeto. El sistema se encuentra en el registro de Windows y cárguelo. C++ / c++ / proyecto de CLI puede usar un objeto COM de la misma manera, o agregando una referencia a él desde el **agregar referencias > COM** lista y usarlo a través de su [contenedor RCW](/dotnet/framework/interop/runtime-callable-wrapper). 

## <a name="net-assemblies-and-windows-runtime-components"></a>Ensamblados .NET y componentes de Windows en tiempo de ejecución

En UWP o C++ / c++ / proyectos de la CLI, consumir ensamblados .NET o componentes de Windows en tiempo de ejecución mediante la adición de un *referencia* al ensamblado o componente. En el **referencias** nodo en un UWP o C++ / c++ / proyecto CLI, consulte las referencias a componentes usados. Haga doble clic en el **referencias** nodo **el Explorador de soluciones** para que aparezca el **Administrador de referencias** y examinar los componentes adicionales que se sabe que el sistema. Haga clic en el **examinar** botón para navegar a cualquier carpeta donde se encuentra un componente personalizado. Dado que los ensamblados de .NET y componentes de Windows en tiempo de ejecución contienen información de tipo integrado, puede ver sus clases y métodos con el botón secundario y eligiendo **ver en el Explorador de objetos**. 

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

### <a name="assembly-reference-properties-ccli"></a>Propiedades de la referencia de ensamblado (C++ / c++ / CLI)

Propiedades de la referencia de ensamblado sólo están disponibles para las referencias a ensamblados de .NET Framework en C / c++ / proyectos de la CLI. Estas propiedades se muestran únicamente cuando se selecciona un ensamblado de .NET Framework en el **referencias** panel. No se pueden modificar las propiedades.

- **Ruta relativa**

   Muestra la ruta de acceso relativa desde el directorio del proyecto hasta el ensamblado al que se hace referencia.

### <a name="build-properties"></a>Propiedades de compilación

Las propiedades siguientes están disponibles en diversos tipos de referencia. Estas propiedades permiten especificar cómo compilar con referencias.

- **Copia local**

   Especifica si se debe copiar automáticamente el ensamblado al que se hace referencia en la ubicación de destino durante una compilación.

- **Copiar ensamblados satélite locales (C++ / c++ / CLI)**

   Especifica si se deben copiar automáticamente los ensamblados satélite del ensamblado al que se hace referencia en la ubicación de destino durante una compilación. Solo se utiliza si el valor de **Copia local** es **true**.

- **Salida de ensamblado de referencia**

   Especifica que este ensamblado se usa en el proceso de compilación. Si el valor es **true**, el ensamblado se agregará a la línea de comandos del compilador durante la compilación.

### <a name="project-to-project-reference-properties"></a>Propiedades de referencia de proyecto a proyecto

Las siguientes propiedades definen una *referencia de proyecto a proyecto* desde el proyecto que está seleccionado en el **referencias** panel a otro proyecto en la misma solución. Para más información, vea [Administrar referencias en un proyecto](/visualstudio/ide/managing-references-in-a-project).

- **Dependencias de la biblioteca de vínculos**

   Cuando esta propiedad es **True**, el sistema de proyectos vincula dentro del proyecto dependiente los archivos .lib generados por el proyecto independiente. Por lo general, usted especificará **True**.

- **Identificador del proyecto**

   Identifica de forma única el proyecto independiente. El valor de propiedad es un GUID de sistema interno que no se puede modificar.

- **Usar entradas de dependencia de biblioteca**

   Cuando esta propiedad es **False**, el sistema de proyectos no vincula dentro del proyecto dependiente los archivos .obj de la biblioteca generada por el proyecto independiente. Por lo tanto, este valor deshabilita la vinculación incremental. Normalmente especificará **False** , porque compilar la aplicación puede tardar mucho tiempo si hay muchos proyectos independientes.

### <a name="read-only-reference-properties-com--net"></a>Propiedades de referencia de solo lectura (COM y. NET)

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

[Referencia de página de propiedades de proyecto de C++](reference/property-pages-visual-cpp.md)<br>
[Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](working-with-project-properties.md)