---
title: Compilador advertencia (nivel 1) C4819 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4819
dev_langs:
- C++
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac468bc605c261b66f47fdf40efd1a01a5383d58
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074284"
---
# <a name="compiler-warning-level-1-c4819"></a>Advertencia del compilador (nivel 1) C4819

El archivo contiene un carácter que no se puede representar en la página de códigos actual (número). Guarde el archivo en formato Unicode para evitar la pérdida de datos.

C4819 se produce cuando un archivo de código fuente ANSI se compila en un sistema con una página de códigos que no puede representar todos los caracteres del archivo.

Para resolver C4819, guarde el archivo en formato Unicode. En Visual Studio, elija **archivo**, **opciones avanzadas para guardar**. En el **opciones avanzadas para guardar** cuadro de diálogo, seleccione una codificación que puede representar todos los caracteres en el archivo, por ejemplo, UTF-8 y, a continuación, elija **Aceptar**.