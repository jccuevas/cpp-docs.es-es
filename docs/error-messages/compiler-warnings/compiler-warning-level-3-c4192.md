---
title: Compilador advertencia (nivel 3) C4192 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4192
dev_langs:
- C++
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 671a8c83dcadcaa89372e53b6c3d677c5810b4a5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114415"
---
# <a name="compiler-warning-level-3-c4192"></a>Compilador advertencia (nivel 3) C4192

exclusión automática durante la importación de biblioteca de tipos 'library' de 'name'

Un `#import` biblioteca contiene un elemento, *nombre*, que se define también en los encabezados de sistema de Win32. Debido a limitaciones de las bibliotecas de tipos, nombres como **IUnknown** o GUID a menudo se definen en una biblioteca de tipos, duplicando la definición de los encabezados de sistema. `#import` detectará estos elementos e incorporarlos en los archivos de encabezado .tlh y. TLI.

Para invalidar este comportamiento, use `#import` atributos [no_auto_exclude](../../preprocessor/no-auto-exclude.md) y [include()](../../preprocessor/include-parens.md).