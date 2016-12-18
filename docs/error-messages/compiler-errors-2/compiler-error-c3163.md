---
title: "Error del compilador C3163 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3163"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3163"
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3163
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'construcción': atributos incoherentes con la declaración anterior  
  
 Los atributos aplicados a una definición están en conflicto con los atributos aplicados a una declaración.  
  
 Una manera de resolver el error C3163 es eliminar los atributos en la declaración adelantada.  Cualquier atributo en una declaración adelantada debe ser menor que los atributos de la definición o, como máximo, igual a ellos.  
  
 Una posible causa del error C3163 implica el lenguaje de anotación de código fuente de Microsoft \(SAL\).  Las macros SAL no se expanden a menos que se compile el proyecto mediante la marca **\/analyze**.  Un programa que compila claramente sin \/analyze podría producir el error C3163 si intenta volver a compilar con la opción \/analyze.  Para obtener más información sobre SAL, vea [Anotaciones de SAL](../../c-runtime-library/sal-annotations.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3163.  
  
```  
// C3163.cpp  
// compile with: /clr /c  
using namespace System;  
  
[CLSCompliant(true)] void f();  
[CLSCompliant(false)] void f() {}   // C3163  
// try the following line instead  
// [CLSCompliant(true)] void f() {}  
```  
  
## Vea también  
 [Anotaciones de SAL](../../c-runtime-library/sal-annotations.md)