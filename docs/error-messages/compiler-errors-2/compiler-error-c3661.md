---
title: Error del compilador C3661
ms.date: 11/04/2016
f1_keywords:
- C3661
helpviewer_keywords:
- C3661
ms.assetid: 50793fd1-1829-4b29-ad0d-094ef2068b43
ms.openlocfilehash: 5edda7eaf50dc4fca60f47128dc97de5d3a1a395
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200382"
---
# <a name="compiler-error-c3661"></a>Error del compilador C3661

la lista de invalidaciones explícitas no encontró ningún método para invalidar

Una invalidación explícita especificó uno o más nombres de tipo.  Sin embargo, no había ninguna función con la signatura necesaria en los tipos que coincidían con la firma de la función de reemplazo.  Si intenta invalidar basándose en el nombre de tipo, debe haber una o varias funciones virtuales en los tipos especificados que coincidan con la firma de la función de reemplazo.

Para obtener más información, vea [invalidaciones explícitas](../../extensions/explicit-overrides-cpp-component-extensions.md).
