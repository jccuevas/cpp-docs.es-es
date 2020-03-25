---
title: Error del compilador C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 00952e55f1b732bd9af3733f5c0ec575a39116fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202117"
---
# <a name="compiler-error-c2818"></a>Error del compilador C2818

la aplicación de ' operator-> ' sobrecargada es recursiva a través del tipo ' type '

Una nueva definición del operador de acceso a miembros de clase contiene una instrucción `return` recursiva. Para volver a definir el operador de `->` con recursividad, debe trasladar la rutina recursiva a una función independiente llamada desde la función de invalidación de operador.
