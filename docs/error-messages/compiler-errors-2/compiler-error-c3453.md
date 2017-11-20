---
title: Error del compilador C3453 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3453
dev_langs: C++
helpviewer_keywords: C3453
ms.assetid: dbefdbcf-f697-4239-b7a5-1d99b85e9e7f
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a9dfd380a55d9233d0b421372e65fc3331c49cc9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3453"></a>Error del compilador C3453
'attribute': atributo no aplicado porque el calificador 'assembly' no coincidía  
  
 Los atributos de ensamblado o de nivel de módulo pueden especificarse como instrucciones independientes.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3453.  
  
```  
// C3453.cpp  
// compile with: /clr /c  
[assembly:System::CLSCompliant(true)]   // C3453  
// try the following line instead  
// [assembly:System::CLSCompliant(true)];  
ref class X {};  
```