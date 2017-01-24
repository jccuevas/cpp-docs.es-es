---
title: "Changing the Default Class Factory and Aggregation Model | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregation [C++], aggregation models"
  - "aggregation [C++], utilizar ATL"
  - "CComClassFactory class, making the default"
  - "CComCoClass class, default class factory and aggregation model"
  - "class factories, cambiar elementos predeterminados"
  - "default class factory"
  - "default class factory, ATL"
  - "valores predeterminados [C++], aggregation model in ATL"
  - "valores predeterminados [C++], class factory"
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing the Default Class Factory and Aggregation Model
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL utiliza [CComCoClass](../atl/reference/ccomcoclass-class.md) para definir el modelo predeterminado de generador y la agregación de clase del objeto.  `CComCoClass` especifica las dos macros siguientes:  
  
-   [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md) declara el generador de la clase se [CComClassFactory](../atl/reference/ccomclassfactory-class.md).  
  
-   [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md) declara que el objeto puede agregarse.  
  
 Puede reemplazar cualquiera de estos valores predeterminados especificando otra macro en la definición de clase.  Por ejemplo, para utilizar [CComClassFactory2](../atl/reference/ccomclassfactory2-class.md) en lugar de `CComClassFactory`, especifique la macro de [DECLARE\_ CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) :  
  
 [!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/CPP/changing-the-default-class-factory-and-aggregation-model_1.h)]  
  
 Otras dos macros que definen un generador de clases son [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) y [DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md).  
  
 ATL también utiliza el mecanismo de `typedef` para implementar el comportamiento predeterminado.  Por ejemplo, la macro de `DECLARE_AGGREGATABLE` utiliza `typedef` para definir un tipo denominado **\_CreatorClass**, que se hace referencia en ATL.  Observe que en una clase derivada, `typedef` utilizando el mismo nombre que los resultados de `typedef` de clase base en ATL mediante la definición y reemplazar el comportamiento predeterminado.  
  
## Vea también  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)   
 [Aggregation and Class Factory Macros](../atl/reference/aggregation-and-class-factory-macros.md)