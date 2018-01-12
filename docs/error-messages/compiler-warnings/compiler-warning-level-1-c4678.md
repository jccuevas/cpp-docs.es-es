---
title: Compilador advertencia (nivel 1) C4678 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4678
dev_langs: C++
helpviewer_keywords: C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7648101a0862aa2006feff73a5ebe32bd0f424a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4678"></a>Advertencia del compilador (nivel 1) C4678
la clase base 'base_type' es menos accesible que 'derived_type'  
  
Un tipo público se deriva de un tipo privado. Si se crea una instancia del tipo público en un ensamblado al que se ha hecho referencia, los miembros del tipo base privado no estarán accesibles.  
  
Solo es accesible mediante la opción del compilador obsoleta C4678 **/CLR: oldSyntax**. Es un error cuando se usa **/CLR**, tener una clase base que es menos accesible que su clase derivada.  
