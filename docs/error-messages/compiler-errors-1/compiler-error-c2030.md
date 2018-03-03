---
title: Error del compilador C2030 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2030
dev_langs:
- C++
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c025fe57d411ae4744a10fe9bc062b336e189e83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2030"></a>Error del compilador C2030
un destructor con accesibilidad 'protected private' no puede ser miembro de una clase declarada 'sealed'  
  
 Una clase de Windows en tiempo de ejecución declarada como `sealed` no puede tener un destructor privado protegido. En tipos sealed solo se permiten destructores no virtuales privados y virtuales públicos. Para obtener más información, consulte [clases y structs Ref](../../cppcx/ref-classes-and-structs-c-cx.md).  
  
 Para corregir este error, cambie la accesibilidad del destructor.