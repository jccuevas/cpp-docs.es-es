---
title: Error del compilador C2818 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2818
dev_langs:
- C++
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f692f52477c988c277f60a689dac5ce83a90acb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112049"
---
# <a name="compiler-error-c2818"></a>Error del compilador C2818

aplicación de sobrecargado 'operator ->' es recursiva mediante el tipo 'type'

Una nueva definición de operador de acceso de miembro de clase contiene una recursiva `return` instrucción. Para volver a definir el `->` operador con la recursión, debe mover la rutina recursiva a una función independiente que se llama desde el operador de reemplazar la función.