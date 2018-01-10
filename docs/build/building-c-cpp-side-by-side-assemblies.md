---
title: Generar ensamblados de C o C++ Side-by-side | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4c54f0e3b8bceff3daa92ecb3e0ee46d7fbeb666
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="building-cc-side-by-side-assemblies"></a>Compilar ensamblados simultáneos de C/C++
A [ensamblado side-by-side](http://msdn.microsoft.com/library/windows/desktop/ff951640) es una colección de recursos: un grupo de archivos DLL, clases de ventanas, servidores COM, bibliotecas de tipos o interfaces: disponibles para una aplicación para usar en tiempo de ejecución. La ventaja principal de volver a empaquetar archivos DLL en ensamblados es que varias versiones de ensamblados pueden ser utilizadas por aplicaciones al mismo tiempo y es posible a los ensamblados de servicio instalado actualmente en el caso de una versión de actualización.  
  
 Una aplicación de Visual C++ puede utilizar uno o varios archivos DLL en diferentes partes de la aplicación. En tiempo de ejecución, los archivos DLL se cargan en el proceso principal y se ejecuta el código necesario. La aplicación se basa en el sistema operativo para buscar los archivos DLL solicitados, comprender lo que posee otro archivos DLL dependientes cargar y, a continuación, cargarlos junto con el archivo DLL solicitado. En las versiones de sistemas operativos Windows anteriores a Windows XP, Windows Server 2003 y Windows Vista, el cargador del sistema operativo busca archivos DLL dependientes en la carpeta local de la aplicación o en otra carpeta especificada en la ruta de acceso del sistema. En Windows XP, Windows Server 2003 y Windows Vista, el cargador del sistema operativo también puede buscar archivos DLL dependientes mediante una [manifiesto](http://msdn.microsoft.com/library/windows/desktop/aa375365) archivo y busque los ensamblados en paralelo que contengan dichos archivos DLL.  
  
 De manera predeterminada, cuando se genera un archivo DLL con Visual Studio, tiene un [manifiesto de aplicación](http://msdn.microsoft.com/library/windows/desktop/aa374191) incrustado como un recurso del tipo RT_MANIFEST con un identificador igual a 2. Como ocurre con un archivo ejecutable, este manifiesto describe las dependencias de este archivo DLL en otros ensamblados. Se supone que el archivo DLL no forma parte de un ensamblado en paralelo y las aplicaciones que dependen de este archivo DLL no se van a usar un manifiesto de aplicación para cargarlo, pero en su lugar se basan en el cargador del sistema operativo para buscar este archivo DLL en la ruta de acceso del sistema.  
  
> [!NOTE]
>  Es importante para un archivo DLL que utiliza un manifiesto de aplicación para que el manifiesto incrustado como un recurso con un identificador igual a 2. Si el archivo DLL se carga dinámicamente en tiempo de ejecución (por ejemplo, si se usa el [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175) función), el cargador del sistema operativo carga los ensamblados dependientes especificados en el manifiesto del archivo DLL. Un manifiesto de aplicación externo para archivos DLL no se comprueba durante un `LoadLibrary` llamar. Si no se incrusta el manifiesto, el cargador puede intentar cargar las versiones incorrectas de ensamblados o no se pudo buscar para buscar los ensamblados dependientes.  
  
 Uno o varios relacionados pueden volver a empaquetar archivos DLL en un ensamblado en paralelo con su correspondiente [manifiesto del ensamblado](http://msdn.microsoft.com/library/windows/desktop/aa374219), que describe qué archivos forman el ensamblado, así como la dependencia del ensamblado en otro side-by-side ensamblados.  
  
> [!NOTE]
>  Si un ensamblado contiene un archivo DLL, se recomienda para incrustar el manifiesto del ensamblado en este archivo DLL como un recurso con un identificador igual a 1 y asignar al ensamblado privado el mismo nombre que el archivo DLL. Por ejemplo, si el nombre del archivo DLL es mylibrary.dll, que utiliza el valor del atributo name en el \<assemblyIdentity > elemento del manifiesto podría ser también mylibrary. En algunos casos, cuando una biblioteca tiene una extensión que no es .dll (por ejemplo, un proyecto de controles ActiveX de MFC crea una biblioteca .ocx) se puede crear un manifiesto de ensamblado externo. En este caso, el nombre del ensamblado y el manifiesto debe ser distinto del nombre del archivo DLL (por ejemplo, MyAssembly, MyAssembly.manifest y mylibrary.ocx). Sin embargo, todavía se recomienda cambiar el nombre de dichas bibliotecas para que tengan la extensión.dll e incrustar el manifiesto como un recurso para reducir el costo de mantenimiento futuras de este ensamblado. Para obtener más información sobre cómo el sistema operativo busca ensamblados privados, vea [Assembly Searching Sequence](http://msdn.microsoft.com/library/windows/desktop/aa374224).  
  
 Este cambio puede permitir la implementación de los archivos DLL correspondientes como un [ensamblado privado](http://msdn.microsoft.com/library/windows/desktop/aa370850) en una carpeta local de la aplicación o como un [ensamblado compartidos](http://msdn.microsoft.com/library/windows/desktop/aa371839) en la caché de ensamblados WinSxS. Tienen varios pasos que deben seguir para conseguir un comportamiento correcto en tiempo de ejecución de este nuevo ensamblado; se describen en [directrices para crear ensamblados de Side-by-side](http://msdn.microsoft.com/library/windows/desktop/aa375155). Después de que se ha creado correctamente un ensamblado que pueda implementar como cualquier un ensamblado compartido o privado junto con una aplicación que dependa de él. Al instalar ensamblados en paralelo como un ensamblado compartido, se pueden seguir las instrucciones descritas en [instalar ensamblados Win32 para uso compartido de forma simultánea en Windows XP](http://msdn.microsoft.com/library/windows/desktop/aa369532) o use [demódulosdecombinación](http://msdn.microsoft.com/library/windows/desktop/aa369820). Al instalar a ensamblados en paralelo como un ensamblado privado, basta con copiar el correspondiente archivo DLL, recursos y manifiesto del ensamblado como parte del proceso de instalación en la carpeta local de la aplicación en el equipo de destino, asegurándose de que este ensamblado puede ser se encontró el cargador en tiempo de ejecución (vea [Assembly Searching Sequence](http://msdn.microsoft.com/library/windows/desktop/aa374224)). Otra forma consiste en usar [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688) y siga las instrucciones descritas en [instalar ensamblados de Win32 para el uso privado de una aplicación en Windows XP](http://msdn.microsoft.com/library/windows/desktop/aa369534).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplos de implementación](../ide/deployment-examples.md)   
 [Creación de C/C++ de aplicaciones aisladas](../build/building-c-cpp-isolated-applications.md)   
 [Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)