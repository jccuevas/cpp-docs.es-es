---
title: Generar ensamblados de C o C++ Side-by-side | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93e02ee27fb8b5a1f4f4f7b2e435a737e1c637a2
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083849"
---
# <a name="building-cc-side-by-side-assemblies"></a>Compilar ensamblados simultáneos de C/C++

Un [side-by-side ensamblado](/windows/desktop/SbsCs/about-side-by-side-assemblies-) es una colección de recursos: un grupo de archivos DLL, clases de windows, servidores COM, bibliotecas de tipos o interfaces, disponibles para una aplicación para usar en tiempo de ejecución. La principal ventaja de volver a empaquetar los archivos DLL en ensamblados es que se pueden usar varias versiones de ensamblados de las aplicaciones al mismo tiempo y es posible a los ensamblados de servicio instalado actualmente en el caso de una versión de actualización.

Una aplicación de Visual C++ puede utilizar uno o varios archivos DLL en distintas partes de la aplicación. En tiempo de ejecución, los archivos DLL se cargan en el proceso principal y se ejecuta el código necesario. La aplicación se basa en el sistema operativo para buscar los archivos DLL solicitados, saber qué otros archivos DLL dependientes debe cargarse y, a continuación, cargarlos junto con el archivo DLL solicitado. En las versiones de sistemas operativos Windows anteriores a Windows XP, Windows Server 2003 y Windows Vista, el cargador del sistema operativo busca archivos DLL dependientes en la carpeta local de la aplicación o en otra carpeta especificada en la ruta de acceso del sistema. En Windows XP, Windows Server 2003 y Windows Vista, el cargador del sistema operativo también puede buscar archivos DLL dependientes mediante una [manifiesto](https://msdn.microsoft.com/library/windows/desktop/aa375365) archivo y busque los ensamblados en paralelo que contienen estos archivos DLL.

De forma predeterminada, cuando se genera un archivo DLL con Visual Studio, tiene un [manifiesto de aplicación](/windows/desktop/SbsCs/application-manifests) incrustado como recurso del tipo RT_MANIFEST con un identificador igual a 2. Al igual que para un archivo ejecutable, este manifiesto describe las dependencias de este archivo DLL en otros ensamblados. Esto supone que el archivo DLL no forma parte de un ensamblado en paralelo y las aplicaciones que dependen de este archivo DLL no se van a usar un manifiesto de aplicación para cargarlo, pero en su lugar se basan en el cargador del sistema operativo para encontrar este archivo DLL en la ruta de acceso del sistema.

> [!NOTE]
> Es importante para un archivo DLL que usa un manifiesto de aplicación para que el manifiesto incrustado como un recurso con el identificador igual a 2. Si el archivo DLL se carga dinámicamente en tiempo de ejecución (por ejemplo, si se usa el [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya) función), el cargador del sistema operativo carga los ensamblados dependientes especificados en el manifiesto del archivo DLL. Un manifiesto de aplicación externa para archivos DLL no está activado durante un `LoadLibrary` llamar. Si no se incrusta el manifiesto, el cargador puede intentar cargar las versiones incorrectas de ensamblados o no pueden buscar para buscar los ensamblados dependientes.

Uno o varios relacionados se puede volver a empaquetar los archivos DLL en un ensamblado en paralelo con su correspondiente [manifiesto del ensamblado](/windows/desktop/SbsCs/assembly-manifests), que describe qué archivos forman el ensamblado, así como la dependencia del ensamblado en otro side-by-side ensamblados.

> [!NOTE]
> Si un ensamblado contiene un archivo DLL, se recomienda insertar el manifiesto del ensamblado en este archivo DLL como un recurso con el identificador igual a 1 y asignar al ensamblado privado el mismo nombre que el archivo DLL. Por ejemplo, si el nombre del archivo DLL es mylibrary.dll, que usa el valor del atributo name en el \<assemblyIdentity > elemento del manifiesto puede ser mylibrary. En algunos casos, cuando una biblioteca tiene una extensión distinta de .dll (por ejemplo, un proyecto de controles ActiveX de MFC crea una biblioteca .ocx) se puede crear un manifiesto de ensamblado externo. En este caso, el nombre del ensamblado y el manifiesto debe ser diferente del nombre del archivo DLL (por ejemplo, MyAssembly, MyAssembly.manifest y mylibrary.ocx). Sin embargo se recomienda seguir para cambiar el nombre de dichas bibliotecas para que tengan la extensión.dll e incrustar el manifiesto como un recurso para reducir el costo de mantenimiento futuro de este ensamblado. Para obtener más información sobre cómo el sistema operativo busca ensamblados privados, vea [Assembly Searching Sequence](/windows/desktop/SbsCs/assembly-searching-sequence).

Este cambio puede permitir la implementación de archivos DLL correspondientes como un [ensamblado privado](/windows/desktop/Msi/private-assemblies) en una carpeta local de la aplicación o como un [ensamblado compartidos](/windows/desktop/Msi/shared-assemblies) en la caché de ensamblados WinSxS. Tienen varios pasos se deben seguir para lograr un comportamiento correcto en tiempo de ejecución de este nuevo ensamblado; se describen en [directrices para crear ensamblados de Side-by-side](/windows/desktop/SbsCs/guidelines-for-creating-side-by-side-assemblies). Después de crea correctamente un ensamblado se puede implementar como un compartido o privado ensamblado junto con una aplicación que depende de él. Al instalar los ensamblados en paralelo como un ensamblado compartido, se pueden seguir las instrucciones descritas en [instalar ensamblados de Win32 para uso compartido en paralelo en Windows XP](/windows/desktop/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp) o use [módulosdecombinación](https://msdn.microsoft.com/library/windows/desktop/aa369820). Al instalar a los ensamblados en paralelo como un ensamblado privado, basta con copiar el correspondiente archivo DLL, recursos y manifiesto del ensamblado como parte del proceso de instalación en la carpeta local de la aplicación en el equipo de destino, lo que garantiza que este ensamblado puede ser se encontró el cargador en tiempo de ejecución (consulte [Assembly Searching Sequence](/windows/desktop/SbsCs/assembly-searching-sequence)). Otra manera es usar [Windows Installer](/windows/desktop/Msi/windows-installer-portal) y siga las instrucciones descritas en [instalar ensamblados de Win32 para el uso privado de una aplicación en Windows XP](/windows/desktop/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp).

## <a name="see-also"></a>Vea también

[Ejemplos de implementación](../ide/deployment-examples.md)<br/>
[Compilación de aplicaciones aisladas de C/C++](../build/building-c-cpp-isolated-applications.md)<br/>
[Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)