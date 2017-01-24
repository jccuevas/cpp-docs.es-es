---
title: "Utilizar una vista de registros (acceso a datos MFC) | Microsoft Docs"
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
  - "vistas de registros, personalizar el código predeterminado"
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar una vista de registros (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema explica la forma habitual de personalizar el código predeterminado para vistas de registros que ha escrito por el asistente.  Normalmente, le interesa restringir la selección de registros mediante un [filtro](../data/odbc/recordset-filtering-records-odbc.md) o [parámetros](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), tal vez [ordenar](../data/odbc/recordset-sorting-records-odbc.md) los registros o personalizar la instrucción SQL.  
  
 Esta información se aplica a [CRecordView](../mfc/reference/crecordview-class.md) \(ODBC\) y [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) \(DAO\).  
  
 El uso de `CRecordView` o `CDaoRecordView` es muy parecido al uso de [CFormView](../mfc/reference/cformview-class.md).  El enfoque básico consiste en utilizar la vista de registros para mostrar y, tal vez, actualizar los registros de un solo conjunto de registros.  También podría interesarle utilizar conjuntos de registros, como se explica en [Vistas de registros: llenar un cuadro de lista con datos de otro conjunto de registros](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
## Vea también  
 [Vistas de registros \(acceso a datos MFC\)](../data/record-views-mfc-data-access.md)   
 [Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)