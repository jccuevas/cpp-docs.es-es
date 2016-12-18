---
title: "C&#243;mo: Crear una aplicaci&#243;n de confianza parcial quitando la dependencia de la DLL de la biblioteca CRT | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr (opción del compilador) [C++], aplicaciones de confianza parcial"
  - "interoperabilidad [C++], aplicaciones de confianza parcial"
  - "interoperabilidad [C++], aplicaciones de confianza parcial"
  - "ensamblados mixtos [C++], aplicaciones de confianza parcial"
  - "msvcm90[d].dll"
  - "aplicaciones de confianza parcial [C++]"
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear una aplicaci&#243;n de confianza parcial quitando la dependencia de la DLL de la biblioteca CRT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se explica la forma de crear una aplicación de Common Language Runtime de confianza parcial mediante [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)], quitando la dependencia de msvcm90.dll.  
  
 Una aplicación de Visual C\+\+ compilada con **\/clr** tiene una dependencia de msvcm90.dll, que forma parte de la biblioteca en tiempo de ejecución de C.  Si se desea que la aplicación se utilice en un entorno de confianza parcial, CLR forzará la existencia de algunas reglas de seguridad de acceso del código en el archivo DLL.  Por consiguiente, será necesario quitar esta dependencia porque msvcm90.dll contiene código nativo y no se puede imponer en él una directiva de seguridad de acceso del código.  
  
 Si la aplicación no utiliza la funcionalidad de la biblioteca en tiempo de ejecución de C y se desea quitar la dependencia de esta biblioteca del código, es necesario usar la opción del vinculador **\/NODEFAULTLIB:msvcmrt.lib** y establecer un vínculo con ptrustm.lib o ptrustmd.lib.  Estas bibliotecas contienen archivos de objeto para la inicialización y desinicialización de una aplicación, clases de excepción utilizadas por el código de inicialización, y código de control de excepciones administradas.  El vínculo con una de estas bibliotecas quitará cualquier dependencia de msvcm90.dll.  
  
> [!NOTE]
>  El orden de desinicialización de ensamblados puede diferir para las aplicaciones que utilizan las bibliotecas de tipo ptrust.  Para las aplicaciones normales, los ensamblados se suelen descargar en orden inverso al de carga, pero este hecho no se puede garantizar.  Para las aplicaciones de confianza parcial, los ensamblados se suelen descargar en el mismo orden en que se cargan,  pero tampoco se puede garantizar este hecho.  
  
### Para crear una aplicación mixta \(\/clr\) de confianza parcial  
  
1.  Para quitar la dependencia de msvcm90.dll, se debe especificar al vinculador que no incluya esta biblioteca utilizando la opción del vinculador **\/NODEFAULTLIB:msvcmrt.lib**.  Para obtener información sobre cómo se realiza esta acción utilizando el entorno de desarrollo de Visual Studio o mediante programación, vea [\/NODEFAULTLIB \(Omitir bibliotecas\)](../build/reference/nodefaultlib-ignore-libraries.md).  
  
2.  Agregue una de las bibliotecas de tipo ptrustm a las dependencias de entrada del vinculador.  Utilice ptrustm.lib si está compilando la aplicación en modo de lanzamiento.  En modo de depuración, use ptrustmd.lib.  Para obtener información sobre cómo se realiza esta acción utilizando el entorno de desarrollo de Visual Studio o mediante programación, vea [archivos .Lib como entrada del vinculador](../build/reference/dot-lib-files-as-linker-input.md).  
  
## Vea también  
 [Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md)   
 [Inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md)   
 [Compatibilidad con bibliotecas para ensamblados mixtos](../dotnet/library-support-for-mixed-assemblies.md)   
 [\/link \(Pasar opciones al vinculador\)](../build/reference/link-pass-options-to-linker.md)   
 [Seguridad del código nativo y del código de .NET Framework](http://msdn.microsoft.com/es-es/bd61be84-c143-409a-a75a-44253724f784)