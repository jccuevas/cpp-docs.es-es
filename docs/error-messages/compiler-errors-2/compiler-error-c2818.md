---
title: Error del compilador C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: f6e33d0e0ee139138df7d8e11357100b3ec3a1a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388701"
---
# <a name="compiler-error-c2818"></a>Error del compilador C2818

aplicación de sobrecargado 'operator ->' es recursiva mediante el tipo 'type'

Una nueva definición de operador de acceso de miembro de clase contiene una recursiva `return` instrucción. Para volver a definir el `->` operador con la recursión, debe mover la rutina recursiva a una función independiente que se llama desde el operador de reemplazar la función.