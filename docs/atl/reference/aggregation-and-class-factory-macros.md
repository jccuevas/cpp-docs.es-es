---
title: "Aggregation and Class Factory Macros | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregation [C++], ATL macros"
  - "class factories, ATL macros"
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Aggregation and Class Factory Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas macros proporcionan maneras de controlar la agregación y de declarar generadores de clases.  
  
|||  
|-|-|  
|[DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md)|Declara que el objeto puede ser agregado \(valor predeterminado\).|  
|[DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)|Declara el generador de la clase se [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), el generador de clase predeterminado de ATL.|  
|[DECLARE\_CLASSFACTORY\_EX](../Topic/DECLARE_CLASSFACTORY_EX.md)|Declara el objeto generador de clases para el generador de clases.|  
|[DECLARE\_ CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md)|Declara [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) para el generador de clases.|  
|[DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md)|Declara [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) para el generador de clases.|  
|[DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md)|Declara [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) para el generador de clases.|  
|[DECLARE\_GET\_CONTROLLING\_UNKNOWN](../Topic/DECLARE_GET_CONTROLLING_UNKNOWN.md)|declara una función virtual de `GetControllingUnknown` .|  
|[DECLARE\_NOT\_AGGREGATABLE](../Topic/DECLARE_NOT_AGGREGATABLE.md)|Declara que el objeto no se puede agregar.|  
|[DECLARE\_ONLY\_AGGREGATABLE](../Topic/DECLARE_ONLY_AGGREGATABLE.md)|Declara que el objeto debe agregarse.|  
|[DECLARE\_POLY\_AGGREGATABLE](../Topic/DECLARE_POLY_AGGREGATABLE.md)|Comprueba el valor desconocido externo y se declara el objeto aggregatable o no aggregatable, según corresponda.|  
|[DECLARE\_PROTECT\_FINAL\_CONSTRUCT](../Topic/DECLARE_PROTECT_FINAL_CONSTRUCT.md)|Protege el objeto externo de eliminación durante la construcción de un objeto interno.|  
|[DECLARE\_VIEW\_STATUS](../Topic/DECLARE_VIEW_STATUS.md)|Especifica los marcadores de **VIEWSTATUS** al contenedor.|  
  
## Vea también  
 [Macros](../../atl/reference/atl-macros.md)