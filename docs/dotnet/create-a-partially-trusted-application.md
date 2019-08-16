---
title: Procedimiento Crear una aplicación de confianza parcial (C++ / c++ / CLI)
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
ms.openlocfilehash: afdfb8ca11753d7def9d7da6f431082b1a90c345
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209127"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Procedimiento Crear una aplicación de confianza parcial quitando la dependencia de la biblioteca DLL de CRT

En este tema se describe cómo crear una aplicación de Common Language Runtime de confianza parcial mediante Visual C++, quitando la dependencia de msvcm90.dll.

Una aplicación de Visual C++ compilada con **/CLR** tiene una dependencia de msvcm90.dll, que forma parte de la biblioteca de C en tiempo de ejecución. Si desea que la aplicación que se usará en un entorno de confianza parcial, el CLR hará cumplir ciertas reglas de seguridad de acceso de código en el archivo DLL. Por lo tanto, será necesario quitar esta dependencia porque msvcm90.dll contiene código nativo y no se puede aplicar directiva de seguridad de acceso de código en él.

Si la aplicación no utiliza la funcionalidad de la biblioteca en tiempo de ejecución de C y desea quitar la dependencia de esta biblioteca desde el código, deberá usar el **/NODEFAULTLIB:msvcmrt.lib** opción del vinculador y un enlace con ptrustm.lib o ptrustmd.lib. Estas bibliotecas contienen archivos de objeto para la inicialización y desinicialización de una aplicación, las clases de excepción utilizan por el código de inicialización y código de control de excepciones administradas. Vinculación de una de estas bibliotecas quitará cualquier dependencia de msvcm90.dll.

> [!NOTE]
>  El orden de desinicialización de ensamblados puede diferir de las aplicaciones que usan las bibliotecas de tipo ptrust. Para las aplicaciones normales, los ensamblados se suelen descargar en el orden inverso al que se cargan, pero esto no está garantizado. Para las aplicaciones de confianza parcial, los ensamblados se suelen descargar en el mismo orden que se cargan. Esto, además, no está garantizado.

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>Para crear una confianza parcial mixto (/ clr) aplicación

1. Para quitar la dependencia de msvcm90.dll, debe especificar al vinculador que no incluya esta biblioteca utilizando la **/NODEFAULTLIB:msvcmrt.lib** opción del vinculador. Para obtener información sobre cómo hacer esto mediante el entorno de desarrollo de Visual Studio o mediante programación, vea [/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md).

1. Agregue una de las bibliotecas de tipo ptrustm a las dependencias de entrada del vinculador. Utilice ptrustm.lib si va a compilar la aplicación en modo de lanzamiento. Modo de depuración, utilice ptrustmd.lib. Para obtener información sobre cómo hacer esto mediante el entorno de desarrollo de Visual Studio o mediante programación, vea [. Archivos de lib como entrada del vinculador](../build/reference/dot-lib-files-as-linker-input.md).

## <a name="see-also"></a>Vea también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[Compatibilidad con bibliotecas para ensamblados mixtos](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (Pasar opciones al vinculador)](../build/reference/link-pass-options-to-linker.md)
