---
title: Error recuperable A2050 de ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 311aedd0cc739fd862efb0a18cc444b3fb75b165
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316985"
---
# <a name="ml-nonfatal-error-a2050"></a>Error recuperable A2050 de ML

**número real o BCD no permitido**

Se usó un número de punto flotante (real) o una constante decimal codificada binaria (BCD) que no es un inicializador de datos.

Se produjo uno de los siguientes pasos:

- Se usó un número real o un BCD en una expresión.

- Se usó un número real para inicializar una directiva que no sea el valor [DWORD](dword.md), [QWord](qword.md) o [TBYTE](tbyte.md).

- Se usó un BCD para inicializar una directiva que no sea `TBYTE`.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](ml-error-messages.md)
