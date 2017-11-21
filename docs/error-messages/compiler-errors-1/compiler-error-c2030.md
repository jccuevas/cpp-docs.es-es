---
title: Error del compilador C2030 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2030
dev_langs: C++
helpviewer_keywords: C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2efd868160e3ec7e5bf356603cc821a0b07f149
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2030"></a>Error del compilador C2030
un destructor con accesibilidad 'protected private' no puede ser miembro de una clase declarada 'sealed'  
  
 Una clase de Windows en tiempo de ejecución declarada como `sealed` no puede tener un destructor privado protegido. En tipos sealed solo se permiten destructores no virtuales privados y virtuales públicos. Para obtener más información, consulte [clases y structs Ref](../../cppcx/ref-classes-and-structs-c-cx.md).  
  
 Para corregir este error, cambie la accesibilidad del destructor.