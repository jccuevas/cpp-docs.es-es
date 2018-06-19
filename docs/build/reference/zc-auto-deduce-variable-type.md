---
title: '-Zc: auto (deducir tipo de Variable) | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:auto
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caa64f64b75145c850c6f6393570dc3f9ba0b0d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379580"
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (Deducir tipo de variable)

El **/Zc: auto [-]** opción del compilador indica al compilador cómo usar el [palabra clave auto](../../cpp/auto-keyword.md) para declarar las variables. Si especifica la opción predeterminada, **/Zc: Auto**, el compilador deduce el tipo de la variable declarada a partir de su expresión de inicialización. Si especifica **/Zc:auto-**, el compilador asigna la variable a la clase de almacenamiento automático.

## <a name="syntax"></a>Sintaxis

> **/ Zc: Auto**[**-**]  

## <a name="remarks"></a>Comentarios

El estándar C++ define un significado original y uno revisado de la palabra clave `auto`. Antes de [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)], la palabra clave declara una variable en la clase de almacenamiento automática; es decir, una variable que tiene una duración local. A partir de [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)], la palabra clave deduce el tipo de una variable desde una expresión de inicialización de la declaración. Utilice la **/Zc: auto [-]** opción del compilador para indicar al compilador que use el significado original o modificado de la `auto` (palabra clave). El **/Zc: Auto** opción está activada de forma predeterminada. El [/ permisivo-](permissive-standards-conformance.md) opción no cambia la configuración predeterminada de **/Zc: Auto**.

El compilador emite un mensaje de diagnóstico adecuado si el uso de la `auto` actual se contradice con la palabra clave **/Zc: Auto** opción del compilador. Para obtener más información, consulte [palabra clave auto](../../cpp/auto-keyword.md). Para obtener más información acerca de los problemas de conformidad con Visual C++, vea [comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para establecer esta opción del compilador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Agregar **/Zc: Auto** o **/Zc:auto-** a la **opciones adicionales:** panel.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
[Auto (palabra clave)](../../cpp/auto-keyword.md)
