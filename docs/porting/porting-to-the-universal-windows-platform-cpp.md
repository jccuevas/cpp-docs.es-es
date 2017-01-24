---
title: "Migrar a la Plataforma universal de Windows (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Migrar a la Plataforma universal de Windows (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema encontrará información sobre cómo migrar código de C\+\+ existente a la plataforma de aplicación de Windows 10, la Plataforma universal de Windows.  Por *universal* se entiende que el código puede iniciarse en cualquier dispositivo que ejecute Windows 10, incluidos equipos de escritorio, teléfonos, tabletas y futuros dispositivos que ejecuten Windows 10. Con Windows 8.1, una aplicación destinada a Windows 8.1 y Windows Phone 8.1 se creaba mediante una característica especial del sistema denominada proyecto compartido. Las aplicaciones Windows universales no usan este mecanismo, sino que emplean un único proyecto y un único XAML que funcionan bien en cualquier dispositivo que ejecute Windows 10. Puede usar características de diseño dinámico XAML para que la interfaz de la aplicación se adapte a distintos tamaños de pantalla.  
  
 La documentación del Centro de desarrollo de Windows contiene una guía para portar aplicaciones de Windows 8.1 a la Plataforma universal de Windows. Consulte [Mover de Windows Runtime 8 a UWP](http://msdn.microsoft.com/library/windows/apps/dn954974.aspx). Aunque la guía se centra principalmente en el código de C\#, la mayor parte es aplicable a C\+\+. Los procedimientos siguientes contienen información más detallada.  
  
 Este tema contiene los siguientes procedimientos para portar código a UWP.  
  
1.  [Portar una aplicación de la Tienda Windows 8.1 a UWP](#BK_81StoreApp)  
  
2.  [Portar un componente de Windows 8.1 en tiempo de ejecución a UWP](#BK_81Component)  
  
 Si tiene un archivo DLL de Win32 de escritorio clásico, puede llamarlo desde una aplicación UWP si lo desea. Con estos procedimientos puede crear una capa de interfaz de usuario de UWP para una aplicación de C\+\+ de escritorio de Windows clásico o para el código de C\+\+ estándar multiplataforma. Vea [Cómo: utilizar código C\+\+ existente en una aplicación universal de la plataforma Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).  
  
##  <a name="BK_81StoreApp"></a> Portar una aplicación de la Tienda Windows 8.1 a UWP  
 Si tiene una aplicación de la Tienda Windows 8.1, puede usar este procedimiento para que funcione en UWP y en cualquier dispositivo que ejecute Windows 10.  Es buena idea compilar primero el proyecto con [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] como un proyecto de Windows 8.1, para eliminar cualquier problema que surja de los cambios en el compilador y las bibliotecas. Una vez hecho esto, hay dos maneras de convertirlo en un proyecto UWP de Windows 10. La manera más fácil \(como se explica en el siguiente procedimiento\) consiste en crear un proyecto universal de Windows y copiar en él el código existente. Si estaba usando un proyecto universal para Windows 8.1 de escritorio y Windows 8.1 Phone, el proyecto se iniciará con dos diseños diferentes en XAML, pero terminará con un único diseño dinámico ajustado al tamaño de la pantalla. La segunda manera de convertir un proyecto a Windows 10 es editar el archivo de proyecto y el archivo Package.appxmanifest. Este método se explica en [Migrar aplicaciones a la Plataforma universal de Windows \(UWP\)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md).  
  
#### Para portar una aplicación de la Tienda Windows 8.1 a UWP:  
  
1.  Si aún no lo ha hecho, abra el proyecto de aplicación de Windows 8.1 en [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] y siga las instrucciones para actualizar el archivo de proyecto.  
  
     Debe tener instaladas las herramientas de Windows 8.1 incluidas en el programa de instalación de Visual Studio. Si no tiene instaladas estas herramientas, inicie la instalación de Visual Studio desde la ventana Programas y características, elija [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] y, en la ventana de configuración, elija **Modificar**. Localice Herramientas de Windows 8.1, asegúrese de que la opción está seleccionada y haga clic en Aceptar.  
  
2.  Abra la ventana Propiedades del proyecto y, en C\+\+, General, establezca el conjunto de herramientas de la plataforma en v140, las herramientas de compilación para [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)].  
  
3.  Compile el proyecto como un proyecto de Windows 8.1 y solucione cualquier error de compilación. Los errores en esta fase se deben probablemente a cambios importantes en las herramientas de compilación y las bibliotecas. Consulte [Cambios importantes en Visual C\+\+ 2015](../porting/visual-cpp-change-history-2003-20151.md) para obtener una explicación detallada de los cambios que podrían afectar a su código.  
  
     Una vez que el proyecto se genere sin problemas, estará listo para portar a la Plataforma universal de Windows \(Windows 10\).  
  
4.  Cree un nuevo proyecto de aplicación Windows universal con la plantilla en blanco. Puede darle el nombre del proyecto existente, aunque para ello los dos proyectos deben estar en directorios distintos.  
  
5.  Cierre la solución y después, mediante el Explorador de Windows o la línea de comandos, copie los archivos de código \(con extensiones .cpp, .h y .xaml\) del proyecto de Windows 8.1 en la misma carpeta del archivo de proyecto \(.vcxproj\) del proyecto que creó en el paso 1. No copie el archivo Package.appxmanifest y, si tiene código diferente para las versiones de escritorio y teléfono de Windows 8.1, elija cuál porta primero \(tendrá que realizar algún trabajo posterior de adaptación a la otra\). Asegúrese de copiar las carpetas, las subcarpetas y su contenido. Si se le solicita, elija reemplazar todos los archivos con nombres duplicados.  
  
6.  Vuelva a abrir la solución y seleccione **Agregar, Elemento existente** en el menú contextual del nodo de proyecto. Seleccione todos los archivos copiados, excepto los que ya forman parte del proyecto.  
  
     Compruebe todas las subcarpetas y asegúrese de agregar también los archivos que contienen.  
  
7.  Si no utiliza el mismo nombre que el proyecto antiguo, abra el archivo Package.appxmanifest y actualice el Punto de entrada para reflejar el nombre del espacio de nombres para la clase Aplicación.  
  
     El campo **Punto de entrada** del archivo Package.appxmanifest contiene un nombre de ámbito para la clase App, que incluye el espacio de nombres que contiene la clase App. Cuando se crea un proyecto universal de Windows, el espacio de nombres se establece en el nombre del proyecto. Si es distinto del que está en los archivos copiados del proyecto anterior, debe actualizar uno de los dos para que coincidan.  
  
8.  Compile el proyecto y solucione cualquier error de compilación debido a cambios importantes entre las distintas versiones del SDK de Windows.  
  
9. Ejecute el proyecto en el escritorio local. Compruebe que no hay ningún error de implementación, que el diseño de la aplicación es razonable y que funciona correctamente en el escritorio.  
  
10. Si tenía archivos de código y .xaml separados para otro dispositivo, como Windows Phone 8.1, examine este código e identifique dónde difiere del dispositivo estándar. Si la diferencia está solo en el diseño, puede utilizar un Visual State Manager en el código xaml para personalizar la presentación según el tamaño de la pantalla. Para otras diferencias, puede usar secciones de condiciones en el código mediante las siguientes instrucciones \#if.  
  
    ```  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP) #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP) #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP) #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)  
    ```  
  
     Estas instrucciones se aplican respectivamente a las aplicaciones de la tienda de Windows, de la tienda de Windows Phone, a ambas o a ninguna \(solo a las de escritorio clásico de Win32\). Estas macros solo están disponibles en Windows SDK 8.1 y posterior, por lo que si necesita compilar el código con las versiones anteriores de Windows SDK o para otras plataformas, también debería considerar el caso de que ninguna de ellas esté definida.  
  
11. Ejecute y depure la aplicación en un emulador o un dispositivo físico para cada tipo de dispositivo admitido por la aplicación. Para ejecutar un emulador, debe ejecutar Visual Studio en un equipo físico, no en una máquina virtual.  
  
##  <a name="BK_81Component"></a> Portar un componente de Windows 8.1 en tiempo de ejecución a UWP  
 Si tiene un archivo DLL o un componente de tiempo de ejecución de Windows que ya funciona con aplicaciones de la Tienda de Windows 8.1, puede usar este procedimiento para hacer funcionar el componente o DLL en UWP y Windows 10. El procedimiento básico consiste en crear un nuevo proyecto y copiar el código en él.  
  
#### Para migrar un componente de Windows 8.1 en tiempo de ejecución a UWP  
  
1.  En el cuadro de diálogo **Nuevo proyecto** de [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)], busque el nodo **Windows Universal**. Si no ve este nodo, instale primero las [herramientas para Windows 10](http://go.microsoft.com/fwlink/p/?LinkID=617903). Elija la plantilla **Windows Runtime Component**, asigne un nombre al componente y elija el botón **Aceptar**. El nombre del componente se usará como nombre del espacio de nombres, por lo que es posible que quiera usar el mismo nombre que el espacio de nombres de sus proyectos antiguos. Para ello, debe crear el proyecto en una carpeta diferente de la antigua. Si elige un nombre distinto, puede actualizar el nombre del espacio de nombres en los archivos de código generado.  
  
2.  Cierre el proyecto.  
  
3.  Copie todos los archivos de código \(.cpp, .h, .xaml, etc.\) del componente de Windows 8.1 al proyecto recién creado. No copie el archivo Package.appxmanifest.  
  
4.  Compile y corrija los errores provocados por cambios bruscos entre las distintas versiones del SDK de Windows.  
  
## Solución de problemas  
 Puede encontrar varios errores durante el proceso de exportar código a la Plataforma universal de Windows. Estos son algunos de los problemas que podrían surgir.  
  
 **Problemas de configuración del proyecto**  
  
 Podría recibir el error:  
  
```Output  
no se encuentra el ensamblado 'platform.winmd': especifique la ruta de acceso de búsqueda del ensamblado utilizando /AI o estableciendo la variable de entorno LIBPATH  
```  
  
 Si esto ocurre, el proyecto no se está generando como un proyecto de Windows universal. Compruebe el archivo de proyecto y asegúrese de que tiene los elementos XAML correctos que identifican un proyecto como proyecto universal de Windows. Los siguientes elementos deben estar presentes \(el número de versión de la plataforma de destino puede ser diferente\):  
  
```xml  
<AppContainerApplication>true</AppContainerApplication> <ApplicationType>Windows Store</ApplicationType> <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion> <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion> <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
```  
  
 No debería ver este error si ha creado un proyecto nuevo de la Plataforma universal de Windows con Visual Studio.  
  
## Vea también  
 [Visual C\+\+ Porting Guide](../porting/porting-to-the-universal-windows-platform-cpp.md)   
 [Desarrollar aplicaciones para la Plataforma universal de Windows \(UWP\)](../Topic/Develop%20apps%20for%20the%20Universal%20Windows%20Platform%20\(UWP\).md)