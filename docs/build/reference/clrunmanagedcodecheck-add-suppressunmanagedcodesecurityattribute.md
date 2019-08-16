---
title: /CLRUNMANAGEDCODECHECK (Quitar SuppressUnmanagedCodeSecurityAttribute)
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.openlocfilehash: ecc560673a8e98752289ef0e0f89d3abfc1938e4
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837240"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (Quitar SuppressUnmanagedCodeSecurityAttribute)

**/CLRUNMANAGEDCODECHECK** especifica que el enlazador no aplica <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> a las llamadas a `PInvoke` generadas por el enlazador desde código administrado en archivos DLL nativos.

## <a name="syntax"></a>Sintaxis

> **/CLRUNMANAGEDCODECHECK**[ **:NO**]

## <a name="remarks"></a>Comentarios

De forma predeterminada, el enlazador aplica **SuppressUnmanagedCodeSecurityAttribute** a las llamadas a `PInvoke` generadas por el enlazador. Cuando **/CLRUNMANAGEDCODECHECK** está en vigor, se quita **SuppressUnmanagedCodeSecurityAttribute**. Para aplicar de forma explícita **SuppressUnmanagedCodeSecurityAttribute** a las llamadas a `PInvoke` generadas por el enlazador, puede usar **/CLRUNMANAGEDCODECHECK:NO**.

El enlazador solo agrega el atributo a los objetos que se compilan con **/clr** o **/clr:pure**. Pero la opción del compilador **/clr:pure** está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017 y versiones posteriores.

El enlazador genera una llamada a `PInvoke` cuando no encuentra un símbolo administrado que satisfaga una referencia desde un autor de la llamada administrado, pero puede encontrar un símbolo nativo para satisfacer esa referencia. Para más información, sobre `PInvoke`, vea [Llamar a funciones nativas desde código administrado](../../dotnet/calling-native-functions-from-managed-code.md).

Tenga en cuenta que si usa <xref:System.Security.AllowPartiallyTrustedCallersAttribute> en el código, debe establecer **/CLRUNMANAGEDCODECHECK** de forma explícita para quitar el atributo **SuppressUnmanagedCodeSecurity**. Una posible vulnerabilidad de seguridad es que una imagen contenga los atributos **SuppressUnmanagedCodeSecurity** y **AllowPartiallyTrustedCallers**.

Vea [Instrucciones de programación segura para código sin administrar](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) para más información sobre las implicaciones del uso de **SuppressUnmanagedCodeSecurityAttribute**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el nodo **Enlazador**.

1. Seleccione la página de propiedades **Avanzadas**.

1. Modifique la propiedad **Comprobación de código no administrado CLR**.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.

## <a name="see-also"></a>Vea también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del enlazador MSVC](linker-options.md)
