---
title: 'Cómo: crear una aplicación de confianza parcial (C++ / CLI) | Documentos de Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a4a0a4b8b1045a9107158c6e67ecdfa7939b6a08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Cómo: Crear una aplicación de confianza parcial quitando la dependencia de la DLL de la biblioteca CRT
En este tema se describe cómo crear una aplicación de Common Language Runtime de confianza parcial mediante Visual C++, quitando la dependencia de msvcm90.dll.  
  
 Una aplicación de Visual C++ creada con **/CLR** tendrá una dependencia de msvcm90.dll, que forma parte de la biblioteca en tiempo de ejecución de C. Si desea que la aplicación para su uso en un entorno de confianza parcial, el CLR aplicará determinadas reglas de seguridad de acceso a código en el archivo DLL. Por lo tanto, será necesario quitar esta dependencia porque msvcm90.dll contiene código nativo y no se puede aplicar la directiva de seguridad de acceso a código en él.  
  
 Si la aplicación no utiliza la funcionalidad de la biblioteca en tiempo de ejecución de C y desea quitar la dependencia de esta biblioteca desde el código, tendrá que usar el **/NODEFAULTLIB:msvcmrt.lib** opción del vinculador y un enlace con ptrustm.lib o ptrustmd.lib. Estas bibliotecas contienen archivos objeto para la inicialización y desinicialización de una aplicación, clases de excepción usan en el código de inicialización y código de control de excepciones administradas. Vinculación de una de estas bibliotecas quitará cualquier dependencia de msvcm90.dll.  
  
> [!NOTE]
>  El orden de desinicialización de ensamblados puede diferir de las aplicaciones que usan las bibliotecas de tipo ptrust. Para las aplicaciones normales, los ensamblados se suelen descargar en el orden inverso al que se cargan, pero no está garantizado. Para las aplicaciones de confianza parcial, los ensamblados se suelen descargar en el mismo orden que se cargan. Esto, además, no se garantiza.  
  
### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>Para crear una confianza parcial mixto (/ clr) aplicación  
  
1.  Para quitar la dependencia de msvcm90.dll, debe especificar al vinculador que no incluya esta biblioteca utilizando la **/NODEFAULTLIB:msvcmrt.lib** opción del vinculador. Para obtener información sobre cómo hacer esto con el entorno de desarrollo de Visual Studio o mediante programación, vea [/NODEFAULTLIB (Omitir bibliotecas)](../build/reference/nodefaultlib-ignore-libraries.md).  
  
2.  Agregue una de las bibliotecas de tipo ptrustm a las dependencias de entrada del vinculador. Utilice ptrustm.lib si va a compilar la aplicación en modo de lanzamiento. Modo de depuración, utilice ptrustmd.lib. Para obtener información sobre cómo hacer esto con el entorno de desarrollo de Visual Studio o mediante programación, vea [. Lib archivos como entrada del vinculador](../build/reference/dot-lib-files-as-linker-input.md).  
  
## <a name="see-also"></a>Vea también  
 [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)   
 [Inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md)   
 [Compatibilidad con bibliotecas para ensamblados mixtos](../dotnet/library-support-for-mixed-assemblies.md)   
 [/link (Pasar opciones al vinculador)](../build/reference/link-pass-options-to-linker.md)   
