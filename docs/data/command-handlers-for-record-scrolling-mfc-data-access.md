---
title: "Controladores de comandos para el desplazamiento por los registros (acceso a datos MFC) | Microsoft Docs"
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
  - "desplazarse por registros [C++]"
  - "vistas de registros [C++], desplazarse"
  - "desplazarse por registros"
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Controladores de comandos para el desplazamiento por los registros (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases [CRecordView](../mfc/reference/crecordview-class.md) y [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) proporcionan control de comandos predeterminado para los siguientes comandos estándar:  
  
-   **ID\_RECORD\_MOVE\_FIRST**  
  
-   **ID\_RECORD\_MOVE\_LAST**  
  
-   **ID\_RECORD\_MOVE\_NEXT**  
  
-   **ID\_RECORD\_MOVE\_PREV**  
  
 La función de miembro `OnMove` de las clases `CRecordView` y `CDaoRecordView` proporciona control de comandos predeterminado para los cuatro comandos, que se desplazan entre los registros.  Cuando se emiten estos comandos, RFX \(o DFX\) carga el nuevo registro en los campos del conjunto de registros y DDX mueve los valores a los controles del formulario de registro.  Para obtener información sobre RFX, consulte [Intercambio de campos de registros \(RFX\)](../data/odbc/record-field-exchange-rfx.md).  
  
> [!NOTE]
>  Asegúrese de utilizar estos identificadores de comando estándar para todos los objetos de interfaz de usuario asociados a los comandos estándar de exploración de registros.  
  
## Vea también  
 [Permitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)