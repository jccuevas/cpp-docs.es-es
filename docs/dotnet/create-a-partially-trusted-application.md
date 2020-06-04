---
title: 'Cómo: Crear una aplicación de confianza parcial (C++/CLI)'
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
ms.openlocfilehash: 9df3a751f4073472b9495425599aaf43878db99a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364404"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Cómo: Crear una aplicación de confianza parcial quitando la dependencia de la DLL de la biblioteca CRT

En este tema se describe cómo crear una aplicación de Common Language Runtime de confianza parcial mediante Visual C++ quitando la dependencia de msvcm90.dll.

Una aplicación de Visual C++ creada con **/clr** tendrá una dependencia de msvcm90.dll, que forma parte de la biblioteca de C-Runtime. Cuando desee que la aplicación se use en un entorno de confianza parcial, CLR aplicará ciertas reglas de seguridad de acceso de código en el archivo DLL. Por lo tanto, será necesario quitar esta dependencia porque msvcm90.dll contiene código nativo y la directiva de seguridad de acceso de código no se puede aplicar en él.

Si la aplicación no utiliza ninguna funcionalidad de la biblioteca de C-Runtime y desea quitar la dependencia de esta biblioteca del código, tendrá que usar la opción del vinculador **/NODEFAULTLIB:msvcmrt.lib** y vincular con ptrustm.lib o ptrustmd.lib. Estas bibliotecas contienen archivos de objetos para la inicialización y la desinicialización de una aplicación, clases de excepción utilizadas por el código de inicialización y código de control de excepciones administrado. La vinculación en una de estas bibliotecas eliminará cualquier dependencia de msvcm90.dll.

> [!NOTE]
> El orden de la desinicialización del ensamblado puede diferir para las aplicaciones que utilizan las bibliotecas de confianza. Para las aplicaciones normales, los ensamblados normalmente se descargan en el orden inverso en que se cargan, pero esto no está garantizado. Para las aplicaciones de confianza parcial, los ensamblados normalmente se descargan en el mismo orden en que se cargan. Esto, además, no está garantizado.

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>Para crear una aplicación mixta de confianza parcial (/clr)

1. Para quitar la dependencia de msvcm90.dll, debe especificar al vinculador que no incluya esta biblioteca mediante la opción del vinculador **/NODEFAULTLIB:msvcmrt.lib.** Para obtener información sobre cómo hacerlo mediante el entorno de desarrollo de Visual Studio o mediante programación, vea [/NODEFAULTLIB (Ignorar bibliotecas)](../build/reference/nodefaultlib-ignore-libraries.md).

1. Agregue una de las bibliotecas ptrustm a las dependencias de entrada del vinculador. Utilice ptrustm.lib si va a compilar la aplicación en modo de versión. Para el modo de depuración, utilice ptrustmd.lib. Para obtener información sobre cómo hacerlo mediante el entorno de desarrollo de Visual Studio o mediante programación, vea [. Lib Files as Linker Input](../build/reference/dot-lib-files-as-linker-input.md).

## <a name="see-also"></a>Consulte también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Inicialización de Asambleas Mixtas](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[Compatibilidad con bibliotecas para ensamblados mixtos](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (Pasar opciones al vinculador)](../build/reference/link-pass-options-to-linker.md)
