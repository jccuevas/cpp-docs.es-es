---
title: Error recuperable A2050 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2050
dev_langs:
- C++
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd2e0e6c2fc818ef9286fd303c07a26bdd8b4e5a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680676"
---
# <a name="ml-nonfatal-error-a2050"></a>Error recuperable A2050 de ML

**real o número de BCD no permitido**

Se usó no sea un número (real) de punto flotante o una constante decimal codificado en binario (BCD) como un inicializador de datos.

Se produjo alguna de las siguientes acciones:

- Se utilizó un número real o un BCD en una expresión.

- Un número real utilizado para inicializar una directiva distinta [DWORD](../../assembler/masm/dword.md), [QWORD](../../assembler/masm/qword.md), o [TBYTE](../../assembler/masm/tbyte.md).

- Un BCD se usó para inicializar una directiva distinta `TBYTE`.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>