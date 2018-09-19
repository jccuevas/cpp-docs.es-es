---
title: Las herramientas del vinculador LNK4022 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4022
dev_langs:
- C++
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 644e7a9ba26dab15e2bfa2a269f62c04f0510180
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041004"
---
# <a name="linker-tools-warning-lnk4022"></a>Advertencia de las herramientas del vinculador LNK4022

no se puede encontrar una coincidencia única para el símbolo 'symbol'

VÍNCULO o LIB encuentra varias coincidencias para el símbolo dado no representativo y no se pudo resolver la ambigüedad. Se genera ningún archivo de salida (.exe, .dll, .exp o .lib). Esta advertencia va seguida de una advertencia [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) para cada símbolo de duplicar y, por último, va seguido de un error irrecuperable [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).

Para evitar esta advertencia, especifique el símbolo en forma representativa. Ejecute [DUMPBIN](../../build/reference/dumpbin-options.md) en el objeto para ver nombres representativos.