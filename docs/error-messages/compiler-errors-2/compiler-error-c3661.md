---
title: Error del compilador C3661 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3661
dev_langs:
- C++
helpviewer_keywords:
- C3661
ms.assetid: 50793fd1-1829-4b29-ad0d-094ef2068b43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7c7987e9ca84009cc8705c22a8f2ec7c3c89b00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026650"
---
# <a name="compiler-error-c3661"></a>Error del compilador C3661

lista de invalidación explícita no encontró ningún método para invalidar

Invalidación explícita especifica uno o más nombres de tipo.  Sin embargo, no hubo ninguna función con la firma necesaria en los tipos que coinciden con la firma de la función reemplazo.  Si intenta reemplazar según el nombre de tipo, debe haber una o varias funciones virtuales en el tipo especificado que coinciden con la firma de la función de reemplazo.

Para obtener más información, consulte [invalidaciones explícitas](../../windows/explicit-overrides-cpp-component-extensions.md).