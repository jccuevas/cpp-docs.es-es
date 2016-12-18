---
title: "Mostrar y manipular datos en un formulario | Microsoft Docs"
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
  - "datos [MFC]"
  - "datos [MFC], mostrar en un formulario"
  - "mostrar datos [C++], formularios"
  - "formularios [C++], mostrar datos"
  - "ODBC [C++], formularios"
  - "vistas de registros [C++], mostrar datos"
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mostrar y manipular datos en un formulario
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Muchas aplicaciones de acceso a datos seleccionan los datos y los muestran en los campos de un formulario.  La clase de base de datos [CRecordView](../../mfc/reference/crecordview-class.md) proporciona un objeto [CFormView](../../mfc/reference/cformview-class.md) directamente conectado al objeto de conjunto de registros.  La vista de registros utiliza el [intercambio de datos de cuadros de diálogo \(DDX\)](../../mfc/dialog-data-exchange-and-validation.md) para mover los valores de los campos del registro actual desde el conjunto de registros hasta los controles del formulario y para mover información actualizada de vuelta al conjunto de registros.  El conjunto de registros, a su vez, utiliza el intercambio de campos de registros \(RFX\) para mover datos entre los miembros de datos de campo y las columnas correspondientes de una tabla del origen de datos.  
  
 Se puede utilizar el Asistente para aplicaciones MFC o **Agregar clase** \(como se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)\) para crear la clase de vista y su clase de conjunto de registros asociada conjuntamente.  
  
 La vista de registros y el conjunto de registros se destruyen al cerrar el documento.  Para obtener más información sobre vistas de registros, vea [Vistas de registros](../../data/record-views-mfc-data-access.md).  Para obtener más información sobre RFX, vea [Intercambio de campos de registros \(RFX\)](../../data/odbc/record-field-exchange-rfx.md).  
  
## Vea también  
 [ODBC y MFC](../../data/odbc/odbc-and-mfc.md)