---
title: Compilador (nivel 3) Advertencia C4192 | Documentos de Microsoft
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
ms.openlocfilehash: 3bae9b7af95de94b8f667cb09710af21044f8b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4192"></a>Compilador C4192 de advertencia (nivel 3)
exclusión automática al importar la biblioteca de tipos 'library' de 'name'  
  
 A `#import` biblioteca contiene un elemento *nombre*, al que también se define en los encabezados de sistema de Win32. Debido a limitaciones de las bibliotecas de tipos, nombres como **IUnknown** o GUID se definen a menudo en una biblioteca de tipos, duplicando la definición de los encabezados de sistema. `#import` detectará estos elementos y rechazar incorporarlos en los archivos de encabezado .tlh y. TLI.  
  
 Para invalidar este comportamiento, use `#import` atributos [no_auto_exclude](../../preprocessor/no-auto-exclude.md) y [include()](../../preprocessor/include-parens.md).