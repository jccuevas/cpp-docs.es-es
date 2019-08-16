---
title: Error del compilador C3661
ms.date: 11/04/2016
f1_keywords:
- C3661
helpviewer_keywords:
- C3661
ms.assetid: 50793fd1-1829-4b29-ad0d-094ef2068b43
ms.openlocfilehash: e171914bcfd6c59d45a21ca2c005cd41f9a071a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397346"
---
# <a name="compiler-error-c3661"></a>Error del compilador C3661

lista de invalidación explícita no encontró ningún método para invalidar

Invalidación explícita especifica uno o más nombres de tipo.  Sin embargo, no hubo ninguna función con la firma necesaria en los tipos que coinciden con la firma de la función reemplazo.  Si intenta reemplazar según el nombre de tipo, debe haber una o varias funciones virtuales en el tipo especificado que coinciden con la firma de la función de reemplazo.

Para obtener más información, consulte [invalidaciones explícitas](../../extensions/explicit-overrides-cpp-component-extensions.md).