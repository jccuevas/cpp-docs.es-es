---
title: "Persistencia de los controles OLE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles OLE, persistencia"
  - "persistencia, controles OLE"
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
caps.latest.revision: 17
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Persistencia de los controles OLE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una capacidad de controles OLE es la persistencia de la propiedad \(o serialización\), que permite al control OLE lea o escriba valores de propiedad en un archivo o una secuencia.  Una aplicación contenedora puede utilizar la serialización para almacenar los valores de propiedad de un control incluso después de que la aplicación ha destruido el control.  Los valores de propiedad de controles activex se pueden leer del archivo o la secuencia a una nueva instancia del control se crea en un momento posterior.  
  
### Persistencia de controles OLE  
  
|||  
|-|-|  
|[PX\_Blob](../Topic/PX_Blob.md)|Cambia una propiedad de control que almacene los datos de \(BLOB\) de objeto binario grande.|  
|[PX\_Bool](../Topic/PX_Bool.md)|Cambia una propiedad del control de **bool**escrito.|  
|[PX\_Color](../Topic/PX_Color.md)|Cambia una propiedad color de un control.|  
|[PX\_Currency](../Topic/PX_Currency.md)|Cambia una propiedad del control de **CY**escrito.|  
|[PX\_DataPath](../Topic/PX_DataPath.md)|Cambia una propiedad del control de `CDataPathProperty`escrito.|  
|[PX\_Double](../Topic/PX_Double.md)|Cambia una propiedad del control de **double**escrito.|  
|[PX\_Font](../Topic/PX_Font.md)|Cambia una propiedad de fuente de un control.|  
|[PX\_Float](../Topic/PX_Float.md)|Cambia una propiedad del control de **flotante**escrito.|  
|[PX\_IUnknown](../Topic/PX_IUnknown.md)|Cambia una propiedad del control de tipo indefinido.|  
|[PX\_Long](../Topic/PX_Long.md)|Cambia una propiedad del control de **long**escrito.|  
|[PX\_Picture](../Topic/PX_Picture.md)|Cambia una propiedad de imagen de un control.|  
|[PX\_Short](../Topic/PX_Short.md)|Cambia una propiedad del control de **corto**escrito.|  
|[PX\_ULong](../Topic/PX_ULong.md)|Cambia una propiedad del control de **ulong**escrito.|  
|[PX\_UShort](../Topic/PX_UShort.md)|Cambia una propiedad del control de **ushort**escrito.|  
|[PX\_String](../Topic/PX_String.md)|Cambia una propiedad de control de la cadena de caracteres.|  
|[PX\_VBXFontConvert](../Topic/PX_VBXFontConvert.md)|Cambia las propiedades fuente\- relacionadas de un control de VBX en una propiedad de la fuente de controles activex.|  
  
 Además, la función global de `AfxOleTypeMatchGuid` se proporciona para probar una coincidencia entre `TYPEDESC` y GUID especificado.  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)