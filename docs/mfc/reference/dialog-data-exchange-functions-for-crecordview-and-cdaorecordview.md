---
title: "Funciones de intercambio de datos de cuadro de di&#225;logo para CRecordView y CDaoRecordView | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], compatibilidad con intercambio de datos de cuadros de diálogo (DDX)"
  - "bases de datos [C++], compatibilidad con intercambio de datos de cuadros de diálogo (DDX)"
  - "DDX (intercambio de datos de cuadros de diálogo) [C++], compatibilidad con bases de datos"
  - "DDX (intercambio de datos de cuadros de diálogo) [C++], funciones"
  - "DDX_Field (funciones)"
  - "ODBC [C++], compatibilidad con intercambio de datos de cuadros de diálogo (DDX)"
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Funciones de intercambio de datos de cuadro de di&#225;logo para CRecordView y CDaoRecordView
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema muestra las funciones de DDX\_Field utilizadas para intercambiar datos entre [CRecordset](../../mfc/reference/crecordset-class.md) y un formulario de [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) y un formulario de [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .  
  
> [!NOTE]
>  Las funciones de DDX\_Field son las funciones DDX en que se intercambian datos con los controles en un formulario.  Pero a diferencia de DDX, se intercambian datos con los campos del objeto de conjunto de registros asociado de la vista en lugar de con campos de registro propio.  Para obtener más información, vea las clases `CRecordView` y `CDaoRecordView`.  
  
### Funciones de DDX\_Field  
  
|||  
|-|-|  
|[DDX\_FieldCBIndex](../Topic/DDX_FieldCBIndex.md)|Datos enteros de las transferencias entre un miembro de datos de campo de conjunto de registros y el índice de la selección actual en un cuadro combinado de [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|  
|[DDX\_FieldCBString](../Topic/DDX_FieldCBString.md)|Datos de `CString` de las transferencias entre un miembro de datos de campo de conjunto de registros y el control de edición de un cuadro combinado en `CRecordView` o `CDaoRecordView`.  Al mover datos de un conjunto de registros al control, esta función selecciona el elemento del cuadro combinado que empieza con los caracteres de la cadena especificada.|  
|[DDX\_FieldCBStringExact](../Topic/DDX_FieldCBStringExact.md)|Datos de `CString` de las transferencias entre un miembro de datos de campo de conjunto de registros y el control de edición de un cuadro combinado en `CRecordView` o `CDaoRecordView`.  Al mover datos de un conjunto de registros al control, esta función selecciona el elemento del cuadro combinado que coincide exactamente con la cadena especificada.|  
|[DDX\_FieldCheck](../Topic/DDX_FieldCheck.md)|Datos booleanos de las transferencias entre un miembro de datos de campo de conjunto de registros y una casilla en `CRecordView` o `CDaoRecordView`.|  
|[DDX\_FieldLBIndex](../Topic/DDX_FieldLBIndex.md)|Datos enteros de las transferencias entre un miembro de datos de campo de conjunto de registros y el índice de la selección actual en un cuadro de lista en `CRecordView` o `CDaoRecordView`.|  
|[DDX\_FieldLBString](../Topic/DDX_FieldLBString.md)|Administra la transferencia de datos de [CString](../../atl-mfc-shared/reference/cstringt-class.md) entre un control de cuadro de lista y los miembros de datos de campo de un conjunto de registros.  Al mover datos de un conjunto de registros al control, esta función selecciona el elemento del cuadro de lista que empieza con los caracteres de la cadena especificada.|  
|[DDX\_FieldLBStringExact](../Topic/DDX_FieldLBStringExact.md)|Administra la transferencia de datos de `CString` entre un control de cuadro de lista y los miembros de datos de campo de un conjunto de registros.  Al mover datos de un conjunto de registros al control, esta función selecciona el primer elemento que coincide exactamente con la cadena especificada.|  
|[DDX\_FieldRadio](../Topic/DDX_FieldRadio.md)|Datos enteros de las transferencias entre un miembro de datos de campo de conjunto de registros y un grupo de botones de radio en `CRecordView` o `CDaoRecordView`.|  
|[DDX\_FieldScroll](../Topic/DDX_FieldScroll.md)|Establece u obtiene la posición de desplazamiento de un control de barra de desplazamiento en `CRecordView` o `CDaoRecordView`.  Llamada a la función de [DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md) .|  
|[DDX\_FieldText](../Topic/DDX_FieldText.md)|Las versiones sobrecargadas están disponibles para transferir `int`, **UINT**, **long**, `DWORD`, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **flotante**, **double**, **corto**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), y datos de [COleCurrency](../../mfc/reference/colecurrency-class.md) entre un miembro de datos de campo de conjunto de registros y un cuadro de edición de `CRecordView` o `CDaoRecordView`.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)