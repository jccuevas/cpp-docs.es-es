---
title: /CLRUNMANAGEDCODECHECK (agregar SupressUnmanagedCodeSecurityAttribute) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
dev_langs:
- C++
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d0a70ea74851d3a10f9d46b8289098d6fb3fe22
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705379"
---
# <a name="clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (Agregar SupressUnmanagedCodeSecurityAttribute)

**/CLRUNMANAGEDCODECHECK** especifica si el vinculador aplicará <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> a generados por el enlazador `PInvoke` llamadas desde código administrado a DLL nativas.

## <a name="syntax"></a>Sintaxis

> **/CLRUNMANAGEDCODECHECK**[**: N**]

## <a name="remarks"></a>Comentarios

De forma predeterminada, el vinculador aplica la **SuppressUnmanagedCodeSecurityAttribute** a generados por el enlazador `PInvoke` llamadas. Cuando **/CLRUNMANAGEDCODECHECK** está en vigor, **SuppressUnmanagedCodeSecurityAttribute** no se aplica.

El vinculador solo agrega el atributo a los objetos que se compilan con **/CLR** o **/CLR: pure**. Sin embargo, el **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

Un `PInvoke` llamada se genera mediante el vinculador cuando el vinculador no encuentra un símbolo administrado que satisfaga una referencia desde un llamador administrado, pero puede buscar un símbolo nativo para satisfacer esa referencia. Para obtener más información acerca de `PInvoke`, consulte [llamar a funciones nativas desde código administrado](../../dotnet/calling-native-functions-from-managed-code.md).

Tenga en cuenta que si usa <xref:System.Security.AllowPartiallyTrustedCallersAttribute> en el código, debe establecer explícitamente **/CLRUNMANAGEDCODECHECK**. Es posible vulnerabilidad de seguridad si una imagen contiene atributos SuppressUnmanagedCodeSecurity y AllowPartiallyTrustedCallers.

Vea [instrucciones de codificación segura para código no administrado](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) para obtener más información acerca de las implicaciones del uso de **SuppressUnmanagedCodeSecurityAttribute**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Expanda el **propiedades de configuración** nodo.

1. Expanda el **vinculador** nodo.

1. Seleccione el **avanzadas** página de propiedades.

1. Modificar el **comprobación de código no administrado de CLR** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)
- [Opciones del vinculador](../../build/reference/linker-options.md)
