---
title: .SAFESEH
ms.date: 11/05/2019
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: df9798800da293e5e0b4f545a8442380b7ff9408
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397995"
---
# <a name="safeseh-32-bit-masm"></a>. SAFESEH (32 bits MASM)

Registra una función como un controlador de excepciones estructurado. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> **.**  *Identificador* de SAFESEH

## <a name="remarks"></a>Comentarios

El *identificador* debe ser el identificador de un procedimiento [PROC](../../assembler/masm/proc.md) o [EXTRN](../../assembler/masm/extrn.md) definido localmente. No se permite una [etiqueta](../../assembler/masm/label-masm.md) . El. La Directiva SAFESEH requiere la opción de línea de comandos [/SAFESEH](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml. exe.

Para obtener más información acerca de los controladores de excepciones estructurados, vea [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).

Por ejemplo, para registrar un controlador de excepciones seguro, cree un nuevo archivo MASM (como se indica a continuación), ensamble con/SAFESEH y agréguelo a los objetos vinculados.

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
