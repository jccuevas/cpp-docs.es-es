---
title: Error del compilador C3371 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3371
dev_langs:
- C++
helpviewer_keywords:
- C3371
ms.assetid: f7ecf1aa-ed0a-4f73-81e5-62cf98f88ea1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b0d2dd9bed6f719b13737cf4466266197b6e585
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253077"
---
# <a name="compiler-error-c3371"></a>Error del compilador C3371
'idl_module': aquí solo se permite la propiedad 'name'  
  
 El uso de[idl_module](../../windows/idl-module.md) directamente en una declaración de función no puede tener ningún parámetro aparte de name.  
  
 El ejemplo siguiente genera la advertencia C3371:  
  
```  
// C3371.cpp  
[idl_module(name="Name", dllname="Some.dll")];  
[idl_module(name="Name", helpstring="Some help")]   // C3371  
int f1();  
// try  
// [idl_module(name="Name")]  
// int f1();  
  
int main()  
{  
}  
```