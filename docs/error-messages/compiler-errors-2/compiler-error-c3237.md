---
title: Error del compilador C3237 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3237
dev_langs:
- C++
helpviewer_keywords:
- C3237
ms.assetid: 690970c8-e13b-4ff3-96e3-5fd93c4d356b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9e43fc9ecf79443cfbf8147ff5b3c227eda9404
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3237"></a>Error del compilador C3237
'generic_class': una clase genérica no puede ser un atributo personalizado  
  
 Las clases genéricas no pueden ser atributos definidos por el usuario.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3237.  
  
```  
// C3237.cpp  
// compile with: /clr /c  
// C3237 expected  
using namespace System;  
  
generic <class T>  
// Delete the following line to resolve.  
[attribute(AttributeTargets::All, AllowMultiple=true)]  
public ref class GR {};  
```