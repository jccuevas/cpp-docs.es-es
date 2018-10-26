---
title: /CLRUNMANAGEDCODECHECK (quite SuppressUnmanagedCodeSecurityAttribute) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
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
ms.openlocfilehash: 9868f0c35f4a988ac8e0aee8076f232f86c04afd
ms.sourcegitcommit: 072e12d6b7a242765bdcc9afe4a14a284ade01fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/26/2018
ms.locfileid: "50136273"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (quite SuppressUnmanagedCodeSecurityAttribute)

**/CLRUNMANAGEDCODECHECK** especifica que no se aplica el vinculador <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> a generadas por vinculador `PInvoke` llamadas desde código administrado en archivos DLL nativos.

## <a name="syntax"></a>Sintaxis

> **/CLRUNMANAGEDCODECHECK**[**: N**]

## <a name="remarks"></a>Comentarios

De forma predeterminada, el vinculador se aplica el **SuppressUnmanagedCodeSecurityAttribute** a generadas por vinculador `PInvoke` llamadas. Cuando **/CLRUNMANAGEDCODECHECK** está en vigor, **SuppressUnmanagedCodeSecurityAttribute** se quita. Para aplicar explícitamente la **SuppressUnmanagedCodeSecurityAttribute** a generadas por vinculador `PInvoke` llamadas, puede usar **/CLRUNMANAGEDCODECHECK:NO**.

El vinculador solo agrega el atributo a objetos que están compilados con **/CLR** o **/CLR: pure**. Sin embargo, el **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Un `PInvoke` llamada genera el vinculador cuando el enlazador no encuentra un símbolo administrado que satisfaga una referencia desde un llamador administrado, pero puede encontrar un símbolo nativo para satisfacer esa referencia. Para obtener más información acerca de `PInvoke`, consulte [llamar a funciones nativas desde código administrado](../../dotnet/calling-native-functions-from-managed-code.md).

Tenga en cuenta que si usa <xref:System.Security.AllowPartiallyTrustedCallersAttribute> en el código, debe establecer explícitamente **/CLRUNMANAGEDCODECHECK** para quitar el **SuppressUnmanagedCodeSecurity** atributo. Es una posible vulnerabilidad de seguridad si una imagen contiene tanto el **SuppressUnmanagedCodeSecurity** y **AllowPartiallyTrustedCallers** atributos.

Consulte [instrucciones de codificación segura para código no administrado](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) para obtener más información acerca de las implicaciones del uso de **SuppressUnmanagedCodeSecurityAttribute**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el **vinculador** nodo.

1. Seleccione el **avanzadas** página de propiedades.

1. Modificar el **código no administrado CLR comprobar** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)
- [Opciones del vinculador](../../build/reference/linker-options.md)
