---
title: Migrar a la Plataforma universal de Windows (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55fbe59128aef6fbc7df20dd14afd102b493f2fd
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322503"
---
# <a name="porting-to-the-universal-windows-platform-c"></a>Migrar a la Plataforma universal de Windows (C++)

En este tema encontrará información sobre cómo migrar código de C++ existente a la plataforma de aplicación de Windows 10, la Plataforma universal de Windows. Por *universal* se entiende que el código puede iniciarse en cualquier dispositivo que ejecute Windows 10, incluidos equipos de escritorio, teléfonos, tabletas y futuros dispositivos que ejecuten Windows 10. Puede crear un solo proyecto y una sola interfaz de usuario basada en XAML que funcione bien en cualquier dispositivo que ejecute Windows 10. Puede usar características de diseño dinámico XAML para que la interfaz de la aplicación se adapte a distintos tamaños de pantalla.

La documentación del Centro de desarrollo de Windows contiene una guía para portar aplicaciones de Windows 8.1 a la Plataforma universal de Windows. Vea [Portar de Windows Runtime 8 a UWP](/windows/uwp/porting/w8x-to-uwp-root). Aunque la guía se centra principalmente en el código de C#, la mayor parte es aplicable a C++. Los procedimientos siguientes contienen información más detallada.

Este tema contiene los siguientes procedimientos para portar código a UWP.

1. [Portar una aplicación de la Tienda Windows 8.1 a UWP](#BK_81StoreApp)

2. [Portar un componente de Windows 8.1 en tiempo de ejecución a UWP](#BK_81Component)

Si tiene un archivo DLL de Win32 de escritorio clásico, puede llamarlo desde una aplicación UWP si lo desea. Con estos procedimientos puede crear una capa de interfaz de usuario de UWP para una aplicación de C++ de escritorio de Windows clásico o para el código de C++ estándar multiplataforma. Vea [Cómo: utilizar código C++ existente en una aplicación universal de la plataforma Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).

## <a name="BK_81StoreApp"></a> Portar una aplicación de la Tienda Windows 8.1 a UWP

Si tiene una aplicación de la Tienda Windows 8.1, puede usar este procedimiento para que funcione en UWP y en cualquier dispositivo que ejecute Windows 10.  Es buena idea compilar primero el proyecto con Visual Studio 2017 como un proyecto de Windows 8.1, para eliminar cualquier problema que surja de los cambios en el compilador y las bibliotecas. Una vez hecho esto, hay dos maneras de convertirlo en un proyecto UWP de Windows 10. La manera más fácil (como se explica en el siguiente procedimiento) consiste en crear un proyecto universal de Windows y copiar en él el código existente. Si estaba usando un proyecto universal para Windows 8.1 de escritorio y Windows 8.1 Phone, el proyecto se iniciará con dos diseños diferentes en XAML, pero terminará con un único diseño dinámico ajustado al tamaño de la pantalla.

### <a name="to-port-a-windows-81-store-app-to-the-uwp"></a>Para portar una aplicación de la Tienda Windows 8.1 a UWP:

1. Si aún no lo ha hecho, abra el proyecto de aplicación de Windows 8.1 en Visual Studio 2017 y siga las instrucciones para actualizar el archivo de proyecto.

   Debe tener instaladas las herramientas de Windows 8.1 incluidas en el programa de instalación de Visual Studio. Si no tiene instaladas estas herramientas, inicie la instalación de Visual Studio desde la ventana Programas y características, elija Visual Studio 2017 y, en la ventana de configuración, elija **Modificar**. Localice Herramientas de Windows 8.1, asegúrese de que la opción está seleccionada y haga clic en Aceptar.

2. Abra la ventana Propiedades del proyecto y, en C++, General, establezca el conjunto de herramientas de la plataforma en v141, que es para Visual Studio 2017.

3. Compile el proyecto como un proyecto de Windows 8.1 y solucione cualquier error de compilación. Los errores en esta fase se deben probablemente a cambios importantes en las herramientas de compilación y las bibliotecas. Vea [Historial de cambios en Visual C++ 2003-2015](../porting/visual-cpp-change-history-2003-2015.md) para obtener una explicación detallada de los cambios que podrían afectar a su código.

   Una vez que el proyecto se genere sin problemas, estará listo para portar a la Plataforma universal de Windows (Windows 10).

4. Cree un nuevo proyecto de aplicación Windows universal con la plantilla en blanco. Puede darle el nombre del proyecto existente, aunque para ello los dos proyectos deben estar en directorios distintos.

5. Cierre la solución y después, mediante el Explorador de Windows o la línea de comandos, copie los archivos de código (con extensiones .cpp, .h y .xaml) del proyecto de Windows 8.1 en la misma carpeta del archivo de proyecto (.vcxproj) del proyecto que creó en el paso 1. No copie el archivo Package.appxmanifest y, si tiene código diferente para las versiones de escritorio y teléfono de Windows 8.1, elija cuál porta primero (tendrá que realizar algún trabajo posterior de adaptación a la otra). Asegúrese de copiar las carpetas, las subcarpetas y su contenido. Si se le solicita, elija reemplazar todos los archivos con nombres duplicados.

6. Vuelva a abrir la solución y seleccione **Agregar, Elemento existente** en el menú contextual del nodo de proyecto. Seleccione todos los archivos copiados, excepto los que ya forman parte del proyecto.

   Compruebe todas las subcarpetas y asegúrese de agregar también los archivos que contienen.

7. Si no utiliza el mismo nombre que el proyecto antiguo, abra el archivo Package.appxmanifest y actualice el Punto de entrada para reflejar el nombre del espacio de nombres para la clase Aplicación.

   El campo **Punto de entrada** del archivo Package.appxmanifest contiene un nombre de ámbito para la clase App, que incluye el espacio de nombres que contiene la clase App. Cuando se crea un proyecto universal de Windows, el espacio de nombres se establece en el nombre del proyecto. Si es distinto del que está en los archivos copiados del proyecto anterior, debe actualizar uno de los dos para que coincidan.

8. Compile el proyecto y solucione cualquier error de compilación debido a cambios importantes entre las distintas versiones del SDK de Windows.

9. Ejecute el proyecto en el escritorio local. Compruebe que no hay ningún error de implementación, que el diseño de la aplicación es razonable y que funciona correctamente en el escritorio.

10. Si tenía archivos de código y .xaml separados para otro dispositivo, como Windows Phone 8.1, examine este código e identifique dónde difiere del dispositivo estándar. Si la diferencia está solo en el diseño, puede utilizar un Visual State Manager en el código xaml para personalizar la presentación según el tamaño de la pantalla. Para otras diferencias, puede usar secciones de condiciones en el código mediante las siguientes instrucciones #if.

    ```cpp
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
    ```

     Estas instrucciones se aplican respectivamente a las aplicaciones de la Plataforma universal Windows, la tienda de Windows Phone, ambas o ninguna (solo a las de escritorio clásico de Win32). Estas macros solo están disponibles en Windows SDK 8.1 y posterior, por lo que si necesita compilar el código con las versiones anteriores de Windows SDK o para otras plataformas, también debería considerar el caso de que ninguna de ellas esté definida.

11. Ejecute y depure la aplicación en un emulador o un dispositivo físico para cada tipo de dispositivo admitido por la aplicación. Para ejecutar un emulador, debe ejecutar Visual Studio en un equipo físico, no en una máquina virtual.

## <a name="BK_81Component"></a> Portar un componente de Windows 8.1 en tiempo de ejecución a UWP

Si tiene un archivo DLL o un componente de tiempo de ejecución de Windows que ya funciona con aplicaciones de la Tienda de Windows 8.1, puede usar este procedimiento para hacer funcionar el componente o DLL en UWP y Windows 10. El procedimiento básico consiste en crear un nuevo proyecto y copiar el código en él.

### <a name="to-port-a-windows-81-runtime-component-to-the-uwp"></a>Para migrar un componente de Windows 8.1 en tiempo de ejecución a UWP

1. En el cuadro de diálogo **Nuevo proyecto** de Visual Studio 2017, busque el nodo **Windows Universal**. Si no ve este nodo, instale primero las [herramientas para Windows 10](http://go.microsoft.com/fwlink/p/?LinkID=617903) . Elija la plantilla **Windows Runtime Component** , asigne un nombre al componente y elija el botón **Aceptar** . El nombre del componente se usará como nombre del espacio de nombres, por lo que es posible que quiera usar el mismo nombre que el espacio de nombres de sus proyectos antiguos. Para ello, debe crear el proyecto en una carpeta diferente de la antigua. Si elige un nombre distinto, puede actualizar el nombre del espacio de nombres en los archivos de código generado.

2. Cierre el proyectos.

3. Copie todos los archivos de código (.cpp, .h, XAML, etc.) del componente de Windows 8.1 en el proyecto recién creado. No copie el archivo Package.appxmanifest.

4. Compile y corrija los errores provocados por cambios bruscos entre las distintas versiones del SDK de Windows.

## <a name="troubleshooting"></a>Solución de problemas

Puede encontrar varios errores durante el proceso de exportación de código a la Plataforma universal de Windows. Estos son algunos de los problemas que podrían surgir.

### <a name="project-configuration-issues"></a>Problemas de configuración del proyecto

Podría recibir el error:

```Output
could not find assembly 'platform.winmd': please specify the assembly search path using /AI or by setting the LIBPATH environment variable
```

Si esto ocurre, el proyecto no se está generando como un proyecto de Windows universal. Compruebe el archivo de proyecto y asegúrese de que tiene los elementos XAML correctos que identifican un proyecto como proyecto universal de Windows. Los siguientes elementos deben estar presentes (el número de versión de la plataforma de destino puede ser diferente):

```xml
<AppContainerApplication>true</AppContainerApplication>
<ApplicationType>Windows Store</ApplicationType>
<WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
<WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
<ApplicationTypeRevision>10.0</ApplicationTypeRevision>
```

Si ha creado un proyecto nuevo de la Plataforma universal de Windows con Visual Studio, no debería ver este error.

## <a name="see-also"></a>Vea también

[Guía de migración de Visual C++](../porting/porting-to-the-universal-windows-platform-cpp.md)  
[Desarrollar aplicaciones para la Plataforma universal de Windows (UWP)](/visualstudio/cross-platform/develop-apps-for-the-universal-windows-platform-uwp)  
