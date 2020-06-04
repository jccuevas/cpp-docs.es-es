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
ms.openlocfilehash: 5953ad6bdf1d9d1b0070ce83dd1d764799b7440a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317570"
---
# <a name="safeseh-32-bit-masm"></a>. SAFESEH (32 bits MASM)

Registra una función como un controlador de excepciones estructurado. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> **.**  *Identificador* de SAFESEH

## <a name="remarks"></a>Notas

El *identificador* debe ser el identificador de un procedimiento [PROC](proc.md) o [EXTRN](extrn.md) definido localmente. No se permite una [etiqueta](label-masm.md) . El. La Directiva SAFESEH requiere la opción de línea de comandos [/SAFESEH](ml-and-ml64-command-line-reference.md) ml. exe.

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

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
