---
title: . SAFESEH | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d10f3c751fe05c118203bb5eeff6c5cba6ec1c8b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693173"
---
# <a name="safeseh"></a>.SAFESEH

Registra una función como controlador de excepciones estructurado.

## <a name="syntax"></a>Sintaxis

> . Identificador SAFESEH

## <a name="remarks"></a>Comentarios

*identificador* debe ser el Id. de definida localmente [PROC](../../assembler/masm/proc.md) o [EXTRN](../../assembler/masm/extrn.md) procedimiento. Un [etiqueta](../../assembler/masm/label-masm.md) no está permitido. El archivo. SAFESEH (directiva) requiere la [/SAFESEH](../../assembler/masm/ml-and-ml64-command-line-reference.md) opción de línea de comandos de ml.exe.

Para obtener más información acerca de los controladores de excepciones estructurado, consulte [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).

Por ejemplo, para registrar un controlador de excepciones seguros, cree un nuevo archivo MASM (como se indica a continuación), ensamblar con/SAFESEH y agregarlo a los objetos vinculados.

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>