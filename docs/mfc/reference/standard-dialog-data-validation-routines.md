---
title: "Rutinas de validaci&#243;n de datos de cuadros de di&#225;logo est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cuadro de diálogo estándar, rutinas de validación de datos"
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Rutinas de validaci&#243;n de datos de cuadros de di&#225;logo est&#225;ndar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema muestra las rutinas estándar de \(DDV\) de validación de datos de diálogo utilizadas para controles comunes de cuadros de diálogo MFC.  
  
> [!NOTE]
>  Las rutinas de intercambio de datos de diálogo estándar se definen en el archivo de encabezado afxdd\_.h.  Sin embargo, las aplicaciones deben incluir afxwin.h.  
  
### Funciones DDV  
  
|||  
|-|-|  
|[DDV\_MaxChars](../Topic/DDV_MaxChars.md)|Comprueba el número de caracteres de un valor determinado del control no supera el máximo especificado.|  
|[DDV\_MinMaxByte](../Topic/DDV_MinMaxByte.md)|Comprueba un valor determinado del control no supera un intervalo determinado de **byte** .|  
|[DDV\_MinMaxDateTime](../Topic/DDV_MinMaxDateTime.md)|Comprueba un valor determinado del control no supera un intervalo de tiempo determinado.|  
|[DDV\_MinMaxDouble](../Topic/DDV_MinMaxDouble.md)|Comprueba un valor determinado del control no supera un intervalo determinado de **double** .|  
|[DDV\_MinMaxDWord](../Topic/DDV_MinMaxDWord.md)|Comprueba un valor determinado del control no supera un intervalo determinado de **dword** .|  
|[DDV\_MinMaxFloat](../Topic/DDV_MinMaxFloat.md)|Comprueba un valor determinado del control no supera un intervalo determinado de **flotante** .|  
|[DDV\_MinMaxInt](../Topic/DDV_MinMaxInt.md)|Comprueba un valor determinado del control no supera un intervalo determinado de **int** .|  
|[DDV\_MinMaxLong](../Topic/DDV_MinMaxLong.md)|Comprueba un valor determinado del control no supera un intervalo determinado de **long** .|  
|[DDV\_MinMaxLongLong](../Topic/DDV_MinMaxLongLong.md)|Comprueba un valor determinado del control no supera un intervalo determinado de **LONGLONG** .|  
|[DDV\_MinMaxMonth](../Topic/DDV_MinMaxMonth.md)|Comprueba un valor determinado del control no supera un intervalo de fechas determinado.|  
|[DDV\_MinMaxShort](../Topic/DDV_MinMaxShort.md)|Comprueba un valor determinado del control no supera un intervalo determinado de **corto** .|  
|[DDV\_MinMaxSlider](../Topic/DDV_MinMaxSlider.md)|Comprueba un valor determinado de control slider esté dentro del intervalo especificado.|  
|[DDV\_MinMaxUInt](../Topic/DDV_MinMaxUInt.md)|Comprueba un valor determinado del control no supera un intervalo determinado de **UINT** .|  
|[DDV\_MinMaxULongLong](../Topic/DDV_MinMaxULongLong.md)|Comprueba un valor determinado del control no supera un intervalo determinado de **ULONGLONG** .|  
  
## Vea también  
 [Rutinas de intercambio de datos de diálogo estándar](../../mfc/reference/standard-dialog-data-exchange-routines.md)   
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)