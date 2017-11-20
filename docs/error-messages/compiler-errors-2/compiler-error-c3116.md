---
title: Error del compilador C3116 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3116
dev_langs: C++
helpviewer_keywords: C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c9503250dd6ff165f6a955d36ebfe38f0715e422
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3116"></a>Error del compilador C3116
'especificador de almacenamiento': clase de almacenamiento no es válida para el método de interfaz  
  
 Se utiliza `typedef`, `register`, o `static` como la clase de almacenamiento para un método de interfaz. Estas clases de almacenamiento no se permiten en los miembros de interfaz.  
  
 El ejemplo siguiente genera C3116:  
  
```  
// C3116.cpp  
__interface ImyInterface  
{  
   static void myFunc();   // C3116  
};  
```