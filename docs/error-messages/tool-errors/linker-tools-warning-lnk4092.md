---
title: "Advertencia de las herramientas del vinculador LNK4092 | Microsoft Docs"
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
  - "LNK4092"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4092"
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4092
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la sección 'sección' compartida modificable contiene reubicaciones; puede que la imagen no se ejecute correctamente  
  
 El vinculador emite esta advertencia siempre que hay una sección compartida para advertir de un problema potencialmente grave.  
  
 Una forma de compartir datos entre varios procesos consiste en marcar una sección como "compartida". Sin embargo, ello puede dar lugar a problemas.  Por ejemplo, si hay una DLL que contiene declaraciones como ésta en una sección de datos compartida:  
  
```  
int var = 1;  
int *pvar = &var;  
```  
  
 El vinculador no puede resolver `pvar` porque su valor depende de la ubicación de la memoria donde se carga la DLL, por lo que inserta un registro de reubicación en la DLL.  Al cargar la DLL en memoria, puede resolverse la dirección de `var` y asignarse `pvar`.  Si otro proceso carga la misma DLL pero no puede cargarla en la misma dirección, la reubicación de la dirección de `var` será actualizada para el segundo proceso, y el primer espacio de dirección del proceso apuntará a la dirección errónea.