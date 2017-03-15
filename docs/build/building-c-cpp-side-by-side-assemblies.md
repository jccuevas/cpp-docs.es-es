---
title: "Compilar ensamblados simult&#225;neos de C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones simultáneas [C++]"
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
caps.latest.revision: 18
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compilar ensamblados simult&#225;neos de C/C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un [ensamblado simultáneo](_win32_side_by_side_assemblies) es una colección de recursos \(un grupo de archivos DLL, clases de ventanas, servidores COM, bibliotecas de tipos o interfaces\) que puede usar una aplicación en tiempo de ejecución.  La ventaja principal de volver a empaquetar archivos DLL en ensamblados es que las aplicaciones pueden utilizar varias versiones de los ensamblados a la vez, y es posible administrar los ensamblados instalados actualmente en caso de una actualización.  
  
 Una aplicación de Visual C\+\+ puede utilizar uno o varios archivos DLL en diferentes partes de la aplicación.  En tiempo de ejecución, los archivos DLL se cargan en el proceso principal y se ejecuta el código necesario.  La aplicación se basa en el sistema operativo para localizar los archivos DLL solicitados, saber qué otros archivos DLL dependientes se han de cargar y, a continuación, cargarlos junto con el archivo DLL solicitado.  En las versiones de los sistemas operativos Windows anteriores a Windows XP, Windows Server 2003 y Windows Vista, el cargador del sistema operativo busca archivos DLL dependientes en la carpeta local de la aplicación o en otra carpeta especificada en la ruta de acceso del sistema.  En Windows XP, Windows Server 2003 y Windows Vista, el cargador del sistema operativo también puede buscar archivos DLL dependientes mediante un archivo de [manifiesto](http://msdn.microsoft.com/library/aa375365) y buscar ensamblados en paralelo que contengan dichos archivos DLL.  
  
 De forma predeterminada, cuando un archivo DLL se compila con Visual Studio, tiene un [manifiesto de aplicación](http://msdn.microsoft.com/library/aa374191) incrustado como recurso del tipo RT\_MANIFEST con un identificador igual a 2.  Como sucede con un archivo ejecutable, este manifiesto describe las dependencias de este archivo DLL en otros ensamblados.  Esto asume que el archivo DLL no forma parte de un ensamblado simultáneo y que las aplicaciones que dependen de este archivo DLL no van a utilizar un manifiesto de aplicación para cargarlo, en su lugar se basan en el cargador del sistema operativo para buscar dicho archivo DLL en la ruta de acceso del sistema.  
  
> [!NOTE]
>  Es importante que un archivo DLL que use un manifiesto de aplicación lo tenga incrustado como recurso con un identificador igual a 2.  Si el archivo DLL se carga dinámicamente en tiempo de ejecución \(por ejemplo, mediante la función [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175)\), el cargador del sistema operativo carga los ensamblados dependientes especificados en el manifiesto del archivo DLL.  Un manifiesto de aplicación externo para archivos DLL no se comprueba durante una llamada a `LoadLibrary`.  Si el manifiesto no está incrustado, el cargador puede que intente cargar versiones incorrectas de ensamblados o que no encuentre ensamblados dependientes.  
  
 Se pueden volver a empaquetar uno o varios archivos DLL relacionados en un ensamblado simultáneo con un [manifiesto del ensamblado](http://msdn.microsoft.com/library/aa374219) correspondiente, el cual describe qué archivos forman dicho ensamblado, así como la dependencia del ensamblado con respecto a otros ensamblados en paralelo.  
  
> [!NOTE]
>  Si un ensamblado contiene un archivo DLL, se recomienda incrustar el manifiesto del ensamblado en este archivo DLL como recurso con un identificador igual a 1, y asignar al ensamblado privado el mismo nombre que el del archivo DLL.  Por ejemplo, si el nombre de archivo es mylibrary.dll, el valor del atributo de nombre utilizado en el elemento assemblyIdentity\> \<de manifiesto también se puede mylibrary.  En algunos casos, si una biblioteca tiene una extensión que no es .dll \(por ejemplo, los proyectos de controles ActiveX de MFC crean una biblioteca .ocx\) se puede crear un manifiesto del ensamblado externo.  En este caso, el nombre del ensamblado y su manifiesto deben ser diferentes del nombre del archivo DLL \(por ejemplo, MyAssembly, MyAssembly.manifest y mylibrary.ocx\).  Sin embargo, aún es recomendable cambiar el nombre de dichas bibliotecas para que tengan la extensión.dll e incrusten el manifiesto como un recurso para reducir el futuro costo de mantenimiento de este ensamblado.  Para obtener más información sobre cómo el sistema operativo busca ensamblados privados, vea [Secuencia de búsqueda de ensamblados](http://msdn.microsoft.com/library/aa374224).  
  
 Este cambio puede permitir la implementación de los archivos DLL correspondientes como un [ensamblado privado](_win32_private_assemblies) en la carpeta local de una aplicación o como un [ensamblado compartido](https://msdn.microsoft.com/en-us/library/aa375996.aspx) en la caché de ensamblados WinSxS.  Se deben seguir varios pasos para lograr un comportamiento correcto en tiempo de ejecución de este nuevo ensamblado; éstos se describen en [Instrucciones para crear ensamblados en paralelo](http://msdn.microsoft.com/library/aa375155).  Después de crear correctamente un ensamblado, se puede implementar como un ensamblado compartido o privado junto con una aplicación que dependa de él.  Al instalar los ensamblados en paralelo como un ensamblado compartido, puede seguir las instrucciones descritas en [Instalación de ensamblados Win32 para uso compartido simultáneo en Windows XP](http://msdn.microsoft.com/library/aa369532) o utilizar [módulos de combinación](http://msdn.microsoft.com/library/aa369820).  Cuando se instalan ensamblados en paralelo como un ensamblado privado, basta con copiar los correspondientes archivos DLL, recursos y manifiesto del ensamblado como parte del proceso de instalación en la carpeta local de la aplicación en el equipo de destino, asegurándose de que el cargador pueda encontrar este ensamblado en tiempo de ejecución \(vea [Secuencia de búsqueda de ensamblados](http://msdn.microsoft.com/library/aa374224)\).  Otra manera es utilizar [Windows Installer](http://msdn.microsoft.com/library/cc185688) y seguir las instrucciones describir en [Instalar Ensamblados Win32 para el uso privado de una aplicación en Windows XP](http://msdn.microsoft.com/library/aa369534).  
  
## Vea también  
 [Ejemplos de implementación](../ide/deployment-examples.md)   
 [Compilar aplicaciones aisladas de C\/C\+\+](../build/building-c-cpp-isolated-applications.md)   
 [Compilar aplicaciones aisladas y ensamblados simultáneos de C\/C\+\+](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)