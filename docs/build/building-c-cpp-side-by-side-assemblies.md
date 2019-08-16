---
title: Compilar ensamblados simultáneos de C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: 6e49ba72a397efb97437a2f7e6d721c782875c48
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493324"
---
# <a name="building-cc-side-by-side-assemblies"></a>Compilar ensamblados simultáneos de C/C++

Un [ensamblado simultáneo](/windows/win32/SbsCs/about-side-by-side-assemblies-) es una colección de recursos (un grupo de archivos dll, clases de Windows, servidores com, bibliotecas de tipos o interfaces) disponible para que una aplicación lo use en tiempo de ejecución. La principal ventaja de volver a empaquetar archivos dll en ensamblados es que las aplicaciones pueden usar varias versiones de los ensamblados al mismo tiempo, y es posible realizar el servicio de los ensamblados instalados actualmente en el caso de una versión de actualización.

Una C++ aplicación puede usar uno o varios archivos dll en diferentes partes de la aplicación. En tiempo de ejecución, los archivos DLL se cargan en el proceso principal y se ejecuta el código necesario. La aplicación se basa en el sistema operativo para localizar los archivos dll solicitados, comprender qué otros archivos DLL dependientes se deben cargar y, a continuación, cargarlos junto con el archivo DLL solicitado. En versiones de sistemas operativos Windows anteriores a Windows XP, Windows Server 2003 y Windows Vista, el cargador del sistema operativo busca archivos DLL dependientes en la carpeta local de la aplicación o en otra carpeta especificada en la ruta de acceso del sistema. En Windows XP, Windows Server 2003 y Windows Vista, el cargador del sistema operativo también puede buscar archivos DLL dependientes mediante un archivo de [manifiesto](/windows/win32/sbscs/manifests) y buscar ensamblados en paralelo que contengan estos archivos dll.

De forma predeterminada, cuando se compila un archivo DLL con Visual Studio, tiene un [manifiesto de aplicación](/windows/win32/SbsCs/application-manifests) incrustado como un recurso de valor de recursos con un identificador igual a 2. Del mismo modo que para un archivo ejecutable, este manifiesto describe las dependencias de este archivo DLL en otros ensamblados. Se supone que el archivo DLL no forma parte de un ensamblado en paralelo y que las aplicaciones que dependen de este archivo DLL no vayan a usar un manifiesto de aplicación para cargarlo, sino que se basan en el cargador del sistema operativo para encontrar este archivo DLL en la ruta de acceso del sistema.

> [!NOTE]
> Es importante que un archivo DLL que use un manifiesto de aplicación tenga el manifiesto incrustado como un recurso con el identificador igual a 2. Si el archivo DLL se carga dinámicamente en tiempo de ejecución (por ejemplo, mediante la función [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) ), el cargador del sistema operativo carga los ensamblados dependientes especificados en el manifiesto del archivo dll. No se comprueba un manifiesto de aplicación externo para archivos dll `LoadLibrary` durante una llamada. Si el manifiesto no está incrustado, el cargador puede intentar cargar versiones incorrectas de los ensamblados o no encontrar para encontrar ensamblados dependientes.

Uno o varios archivos dll relacionados se pueden volver a empaquetar en un ensamblado en paralelo con un [manifiesto](/windows/win32/SbsCs/assembly-manifests)del ensamblado correspondiente, que describe qué archivos forman el ensamblado, así como la dependencia del ensamblado en otros ensamblados en paralelo.

> [!NOTE]
> Si un ensamblado contiene un archivo DLL, se recomienda incrustar el manifiesto del ensamblado en este archivo DLL como un recurso con el identificador igual a 1, y asignar al ensamblado privado el mismo nombre que el archivo DLL. Por ejemplo, si el nombre de la dll es myLibrary. dll, el valor del atributo name usado en el \<elemento assemblyIdentity > del manifiesto también puede ser myLibrary. En algunos casos, cuando una biblioteca tiene una extensión distinta de. dll (por ejemplo, un proyecto de controles ActiveX MFC crea una biblioteca. ocx), se puede crear un manifiesto de ensamblado externo. En este caso, el nombre del ensamblado y su manifiesto deben ser diferentes del nombre del archivo DLL (por ejemplo, myAssembly, myAssembly. manifest y myLibrary. ocx). Sin embargo, se recomienda cambiar el nombre de dichas bibliotecas para que tengan la extensión. dll e insertar el manifiesto como un recurso para reducir el costo de mantenimiento futuro de este ensamblado. Para obtener más información sobre cómo el sistema operativo busca ensamblados privados, vea [secuencia de búsqueda](/windows/win32/SbsCs/assembly-searching-sequence)de ensamblados.

Este cambio puede permitir la implementación de los archivos dll correspondientes como un [ensamblado privado](/windows/win32/Msi/private-assemblies) en una carpeta local de la aplicación o como un [ensamblado compartido](/windows/win32/Msi/shared-assemblies) en la caché de ensamblados de WinSxS. Se deben seguir varios pasos para lograr el comportamiento correcto en tiempo de ejecución de este nuevo ensamblado. se describen en [instrucciones para crear ensamblados en paralelo](/windows/win32/SbsCs/guidelines-for-creating-side-by-side-assemblies). Una vez creado correctamente un ensamblado, se puede implementar como un ensamblado compartido o privado junto con una aplicación que depende de él. Al instalar ensamblados simultáneos como ensamblados compartidos, puede seguir las instrucciones descritas en [Instalar ensamblados Win32 para compartir en paralelo en Windows XP](/windows/win32/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp) o usar [módulos de combinación](/windows/win32/msi/merge-modules). Al instalar ensamblados en paralelo como un ensamblado privado, puede copiar simplemente los archivos DLL, recursos y manifiestos de ensamblado correspondientes como parte del proceso de instalación en la carpeta local de la aplicación en el equipo de destino, asegurándose de que este ensamblado se puede encontrado por el cargador en tiempo de ejecución (vea [secuencia de búsqueda](/windows/win32/SbsCs/assembly-searching-sequence)de ensamblados). Otra manera es usar [Windows Installer](/windows/win32/Msi/windows-installer-portal) y seguir las instrucciones descritas en [Instalar ensamblados Win32 para el uso privado de una aplicación en Windows XP](/windows/win32/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp).

## <a name="see-also"></a>Vea también

[Compilación de aplicaciones aisladas de C/C++](building-c-cpp-isolated-applications.md)<br/>
[Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
