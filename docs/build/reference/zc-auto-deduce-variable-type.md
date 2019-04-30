---
title: /Zc:auto (Deducir tipo de variable)
ms.date: 02/28/2018
f1_keywords:
- /Zc:auto
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
ms.openlocfilehash: ea977020286d720ed3a6b1b13bf8ff8f5c85e5b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315968"
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (Deducir tipo de variable)

El **/Zc: auto [-]** opción del compilador indica al compilador cómo usar el [palabra clave auto](../../cpp/auto-keyword.md) para declarar variables. Si especifica la opción predeterminada, **/Zc: Auto**, el compilador deduce el tipo de la variable declarada a partir de su expresión de inicialización. Si especifica **/Zc:auto-**, el compilador asignará la variable a la clase de almacenamiento automático.

## <a name="syntax"></a>Sintaxis

> **/Zc:auto**[**-**]

## <a name="remarks"></a>Comentarios

El estándar C++ define un significado original y uno revisado de la palabra clave `auto`. Antes de Visual C++ 2010, la palabra clave declara una variable en la clase de almacenamiento automático; es decir, una variable que tiene una duración local. A partir de Visual C++ 2010, la palabra clave deduce el tipo de una variable de expresión de inicialización de la declaración. Utilice la **/Zc: auto [-]** opción del compilador para indicar al compilador que use el significado original o el revisado de la `auto` palabra clave. El **/Zc: Auto** opción está activada de forma predeterminada. El [/ permissive-](permissive-standards-conformance.md) opción no cambia la configuración predeterminada de **/Zc: Auto**.

El compilador emite un mensaje de diagnóstico adecuado si el uso de la `auto` actual se contradice con la palabra clave **/Zc: Auto** opción del compilador. Para obtener más información, consulte [palabra clave auto](../../cpp/auto-keyword.md). Para obtener más información acerca de problemas de conformidad con Visual C++, vea [comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para establecer esta opción del compilador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Agregar **/Zc: Auto** o **/Zc:auto-** a la **opciones adicionales:** panel.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](zc-conformance.md)<br/>
[Auto (palabra clave)](../../cpp/auto-keyword.md)
