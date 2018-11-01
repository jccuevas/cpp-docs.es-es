---
title: Error del compilador C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: f6e33d0e0ee139138df7d8e11357100b3ec3a1a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593445"
---
# <a name="compiler-error-c2818"></a>Error del compilador C2818

aplicación de sobrecargado 'operator ->' es recursiva mediante el tipo 'type'

Una nueva definición de operador de acceso de miembro de clase contiene una recursiva `return` instrucción. Para volver a definir el `->` operador con la recursión, debe mover la rutina recursiva a una función independiente que se llama desde el operador de reemplazar la función.