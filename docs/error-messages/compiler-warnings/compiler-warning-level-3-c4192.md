---
title: Compilador (nivel 3) Advertencia C4192 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4192
dev_langs: C++
helpviewer_keywords: C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 022c0e0aac8d231963ddf6d5d3715d55f726a8b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4192"></a>Compilador C4192 de advertencia (nivel 3)
exclusión automática al importar la biblioteca de tipos 'library' de 'name'  
  
 A `#import` biblioteca contiene un elemento *nombre*, al que también se define en los encabezados de sistema de Win32. Debido a limitaciones de las bibliotecas de tipos, nombres como **IUnknown** o GUID se definen a menudo en una biblioteca de tipos, duplicando la definición de los encabezados de sistema. `#import`detectará estos elementos y rechazar incorporarlos en los archivos de encabezado .tlh y. TLI.  
  
 Para invalidar este comportamiento, use `#import` atributos [no_auto_exclude](../../preprocessor/no-auto-exclude.md) y [include()](../../preprocessor/include-parens.md).