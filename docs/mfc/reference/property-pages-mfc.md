---
title: "P&#225;ginas de propiedades (MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones de transferencia de datos de página de propiedades de MFC"
  - "páginas de propiedades, funciones globales de MFC"
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# P&#225;ginas de propiedades (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las páginas de propiedades muestran los valores actuales de las propiedades específicas de controles activex en un personalizable, de interfaz gráfica para ver y editar admiten un mecanismo de la dato\- asignación basado en el diálogo de intercambio de datos \(DDX\).  
  
 Este mecanismo de la dato\- asignación asigna los controles de la página de propiedades a las propiedades individuales de controles activex.  El valor de la propiedad del control refleja el estado o el contenido del control de la página de propiedades.  La asignación entre los controles de la página de propiedades y las propiedades es especificado por las llamadas de función de **DDP\_** en la función miembro de `DoDataExchange` de la página de propiedades.  A continuación se muestra una lista de **DDP\_** funciona que intercambian datos escritos en la página de propiedades del control:  
  
### Transferencia de datos de la página de propiedades  
  
|||  
|-|-|  
|[DDP\_CBIndex](../Topic/DDP_CBIndex.md)|Enlaza el índice seleccionado de la cadena en un cuadro combinado con la propiedad de un control.|  
|[DDP\_CBString](../Topic/DDP_CBString.md)|Vincula la cadena seleccionado en un cuadro combinado con la propiedad de un control.  La cadena seleccionado puede empezar con las mismas letras que el valor de propiedad pero no tiene que coincidir con él totalmente.|  
|[DDP\_CBStringExact](../Topic/DDP_CBStringExact.md)|Vincula la cadena seleccionado en un cuadro combinado con la propiedad de un control.  La cadena seleccionado y el valor de cadena de propiedad deben coincidir exactamente.|  
|[DDP\_Check](../Topic/DDP_Check.md)|Vincula una casilla en la página de propiedades del control con la propiedad de un control.|  
|[DDP\_LBIndex](../Topic/DDP_LBIndex.md)|Enlaza el índice seleccionado de la cadena en un cuadro de lista con la propiedad de un control.|  
|[DDP\_LBString](../Topic/DDP_LBString.md)|Vincula la cadena seleccionado en un cuadro de lista con la propiedad de un control.  La cadena seleccionado puede empezar con las mismas letras que el valor de propiedad pero no tiene que coincidir con él totalmente.|  
|[DDP\_LBStringExact](../Topic/DDP_LBStringExact.md)|Vincula la cadena seleccionado en un cuadro de lista con la propiedad de un control.  La cadena seleccionado y el valor de cadena de propiedad deben coincidir exactamente.|  
|[DDP\_PostProcessing](../Topic/DDP_PostProcessing.md)|Finalizar la transferencia de valores de propiedad del control.|  
|[DDP\_Radio](../Topic/DDP_Radio.md)|Vincula un grupo de botones de radio en la página de control con la propiedad de un control.|  
|[DDP\_Text](../Topic/DDP_Text.md)|Vincula un control en la página de control con la propiedad de un control.  Esta función controla varios tipos de propiedades, como **double**, **corto**, `BSTR`, y **long**.|  
  
 Para obtener más información sobre las páginas de propiedades de `DoDataExchange` , vea el artículo [Controles ActiveX: Páginas de propiedades](../../mfc/mfc-activex-controls-property-pages.md).  
  
 A continuación se muestra una lista de macros utilizadas para crear y administrar las páginas de propiedades de un control activex:  
  
### Páginas de propiedades  
  
|||  
|-|-|  
|[BEGIN\_PROPPAGEIDS](../Topic/BEGIN_PROPPAGEIDS.md)|Inicia la lista de los id. de la página de propiedades.|  
|[END\_PROPPAGEIDS](../Topic/END_PROPPAGEIDS.md)|Finaliza la lista de los id. de la página de propiedades.|  
|[PROPPAGEID](../Topic/PROPPAGEID.md)|Declara una página de propiedades de la clase de control.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)