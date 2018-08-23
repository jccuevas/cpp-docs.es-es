---
title: Solución de problemas de C o C++ de aplicaciones aisladas y ensamblados en paralelo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56fc61fa7dd7973a6ee1cc4c5a20311bf43b056f
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572108"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>Solucionar problemas de aplicaciones aisladas y ensamblados simultáneos de C/C++
La acción de cargar una aplicación de C/C++ puede sufrir un error si no se pueden encontrar las bibliotecas dependientes. En este artículo se describen algunas de las razones comunes por las que una aplicación de C/C++ no se carga y se sugieren pasos para resolver los problemas.  
  
 Si una aplicación no puede cargarse porque tiene un manifiesto que especifica una dependencia en un ensamblado en paralelo y ese ensamblado no se instala como ensamblado privado en la misma carpeta que el ejecutable o en la memoria caché de ensamblados nativa en la carpeta %WINDIR%\WinSxS\, puede aparecer uno de los siguientes mensajes de error, según la versión de Windows en la que se intente ejecutar la aplicación.  
  
-   La aplicación podría no inicializarse correctamente (0xc0000135).  
  
-   Error de inicio de la aplicación porque la configuración de la misma no es correcta. Si vuelve a instalar la aplicación, puede que se corrijan los problemas.  
  
-   El sistema no puede ejecutar el programa especificado.  
  
 Si la aplicación no tiene ningún manifiesto y depende de un archivo DLL que Windows no puede encontrar en las ubicaciones típicas de búsqueda, puede aparecer un mensaje de error similar al siguiente:  
  
-   Esta aplicación no ha podido iniciar porque *un archivo DLL necesario* no se encontró. La reinstalación de la aplicación puede solucionar el problema.  
  
 Si la aplicación se implementa en un equipo que no tiene Visual Studio, se bloquea y muestra mensajes de error similares a los anteriores, compruebe lo siguiente:  
  
1.  Siga los pasos que se describen en [descripción de las dependencias de una aplicación de Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Dependency Walker puede mostrar la mayoría de las dependencias de una aplicación o de un archivo DLL. Si observa que faltan algunos archivos DLL, instálelos en el equipo en el que está intentando ejecutar la aplicación.  
  
2.  El cargador del sistema operativo utiliza el manifiesto de la aplicación para cargar los ensamblados de los que depende la aplicación. El manifiesto se puede incrustar en el binario como un recurso o se puede instalar como un archivo independiente en la carpeta de la aplicación. Para comprobar si el manifiesto está incrustado en el archivo binario, abra el archivo binario en Visual Studio y busque RT_MANIFEST en su lista de recursos. Si no se encuentra un manifiesto incrustado, busque en la carpeta de aplicación para un archivo que se denomina algo parecido a < nombredebinario >. \<extensión > .manifest.  
  
3.  Si la aplicación depende de ensamblados en paralelo y no existe un manifiesto, debe asegurarse de que el vinculador genere uno para el proyecto. Active la opción del vinculador **Generar manifiesto** en el **las propiedades del proyecto** cuadro de diálogo para el proyecto.  
  
4.  Si el manifiesto está incrustado en el binario, asegúrese de que el identificador de RT_MANIFEST es correcto para este tipo del binario. Para obtener más información sobre el identificador de recurso para usar, consulte [Using Side-by-Side Assemblies como un recurso (Windows)](http://msdn.microsoft.com/library/windows/desktop/aa376617.aspx). Si el manifiesto se encuentra en un archivo independiente, ábralo en un editor XML o en un editor de texto. Para obtener más información sobre los manifiestos y reglas para la implementación, consulte [manifiestos](http://msdn.microsoft.com/library/aa375365).  
  
    > [!NOTE]
    >  Si hay un manifiesto incrustado y un archivo de manifiesto independiente, el cargador del sistema operativo utiliza el manifiesto incrustado y omite el archivo independiente. Sin embargo, en Windows XP, se cumple lo contrario: se usa el archivo de manifiesto independiente y se omite el manifiesto incrustado.  
  
5.  Se recomienda que incruste un manifiesto en cada archivo DLL porque los manifiestos externos se omiten cuando se carga un archivo DLL a través de una llamada a `LoadLibrary`. Para obtener más información, consulte [manifiestos del ensamblado](http://msdn.microsoft.com/library/aa374219).  
  
6.  Compruebe que todos los ensamblados enumerados en el manifiesto estén instalados correctamente en el equipo. Cada ensamblado se especifica en el manifiesto por su nombre, el número de versión y la arquitectura del procesador. Si la aplicación depende de los ensamblados en paralelo, compruebe que estos ensamblados estén instalados correctamente en el equipo para que el cargador del sistema operativo pueda encontrarlos, tal como se describe en [Assembly Searching Sequence](http://msdn.microsoft.com/library/aa374224). Recuerde que los ensamblados de 64 bits no se pueden cargar en procesos de 32 bits ni ejecutarse en sistemas operativos de 32 bits.  
  
## <a name="example"></a>Ejemplo  
 Supongamos que tenemos una aplicación, appl.exe, que se compila con Visual C++. El manifiesto de la aplicación está incrustado en appl.exe como recurso binario RT_MANIFEST con un identificador igual a 1 o está almacenado como archivo independiente appl.exe.manifest. El contenido de este manifiesto se asemeja a lo siguiente:  
  
```  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <dependency>  
    <dependentAssembly>  
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>  
    </dependentAssembly>  
  </dependency>  
</assembly>  
```  
  
 Para el cargador del sistema operativo, este manifiesto expresa que appl.exe depende de un ensamblado denominado Fabrikam.SxS.Library, versión 2.0.20121.0, compilado para una arquitectura de procesador x86 de 32 bits. El ensamblado en paralelo dependiente se puede instalar como un ensamblado compartido o como un ensamblado privado.  
  
 El manifiesto de un ensamblado compartido se instala en la carpeta %WINDIR%\WinSxS\Manifests\. Identifica el ensamblado y muestra su contenido, es decir, los archivos DLL que forman parte del ensamblado:  
  
```  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
   <noInheritable/>  
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>  
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>  
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>  
</assembly>  
```  
  
 También pueden usar los ensamblados en paralelo [archivos de configuración del publicador](http://msdn.microsoft.com/library/aa375682), también conocidos como archivos de directiva, para redirigir globalmente aplicaciones y ensamblados para usar una versión de un ensamblado en paralelo en lugar de otra versión del mismo ensamblado. Puede comprobar las directivas para un ensamblado compartido en la carpeta %WINDIR%\WinSxS\Policies\. A continuación se muestra un archivo de directivas del ejemplo:  
  
```  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  
   <assemblyIdentity type="win32-policy" name="policy.2.0.Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>  
   <dependency>  
      <dependentAssembly>  
         <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>  
         <bindingRedirect oldVersion="2.0.10000.0-2.0.20120.99" newVersion="2.0.20121.0"/>  
      </dependentAssembly>  
   </dependency>  
</assembly>  
```  
  
 Este archivo de directivas especifica que cualquier aplicación o ensamblado que requiera la versión 2.0.10000.0 de este ensamblado debe utilizar en su lugar la versión 2.0.20121.0, que es la versión actual instalada en el sistema. Si se especifica en el archivo de directivas una versión del ensamblado mencionado en el manifiesto de la aplicación, el cargador busca en la carpeta %WINDIR%\WinSxS\ una versión de este ensamblado especificada en el manifiesto y si no está instalada esa versión, la carga sufre un error. Si la versión 2.0.20121.0 del ensamblado no está instalada, la carga sufre un error en las aplicaciones que requieren la versión 2.0.10000.0 del ensamblado.  
  
 Sin embargo, el ensamblado también se puede instalar como un ensamblado en paralelo privado en la carpeta de la aplicación instalada. Si el sistema operativo no encuentra el ensamblado como ensamblado compartido, lo busca como ensamblado privado, en el orden siguiente:  
  
1.  Compruebe la carpeta de un archivo de manifiesto que tiene el nombre de la aplicación \<nombreDeEnsamblado > .manifest. En este ejemplo, el cargador intenta buscar Fabrikam.SxS.Library.manifest en la carpeta que contiene appl.exe. Si encuentra el manifiesto, el cargador carga el ensamblado desde la carpeta de la aplicación. Si no se encuentra el ensamblado, la carga sufre un error.  
  
2.  Intente abrir el \\< assemblyName\>\ en la carpeta que contiene appl.exe, y si \\< assemblyName\>\ existe, intenta cargar un archivo de manifiesto que tiene el nombre \<assemblyName >. manifiesto desde esta carpeta. Si se encuentra el manifiesto, el cargador carga el ensamblado desde el \\< assemblyName\>\ carpeta. Si no se encuentra el ensamblado, la carga sufre un error.  
  
 Para obtener más información sobre cómo el cargador busca ensamblados dependientes, consulte [Assembly Searching Sequence](http://msdn.microsoft.com/library/aa374224). Si el cargador no encuentra un ensamblado dependiente como ensamblado privado, la carga sufre un error y se muestra el mensaje "El sistema no puede ejecutar el programa especificado". Para solucionar este error, asegúrese de que los ensamblados dependientes, y los archivos DLL que forman parte de ellos, estén instalados en el equipo como ensamblados privados o compartidos.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de aplicaciones aisladas y ensamblados en paralelo](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)