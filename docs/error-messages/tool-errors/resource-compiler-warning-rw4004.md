---
title: Advertencia del compilador de recursos RW4004 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0249f7d01ee344f0fa17bdc39e58e9fce26c9b25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-warning-rw4004"></a>Advertencia del compilador de recursos RW4004
Carácter ASCII no equivalente a código de tecla virtual  
  
 Se usó un literal de cadena para el código de tecla virtual en un acelerador de tipo VIRTKEY.  
  
 Esta advertencia permite continuar, pero tenga en cuenta que las teclas de aceleración generadas no pueden coincidir con la cadena indicada. (los aceleradores VIRTKEY usan códigos de tecla distintos que los aceleradores ASCII).  
  
 Aunque los literales de cadena sean válidos sintácticamente, sólo se puede asegurar que se consigue el acelerador deseado mediante la **VK_\* #define** valores en WINDOWS.h.