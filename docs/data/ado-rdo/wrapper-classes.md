---
title: "Clases contenedoras | Microsoft Docs"
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
  - "controles ActiveX [C++], clases contenedoras"
  - "enlace de datos [C++], controles ActiveX"
  - "clases contenedoras [C++], controles ActiveX"
ms.assetid: ebbc17b9-cc1b-4c29-afa9-da7f9511876e
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Clases contenedoras
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Al [insertar un control](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md) en un proyecto de Visual C\+\+, no se incluyen de manera predeterminada las clases contenedoras del mismo.  Sin embargo, si desea [modificar el comportamiento del control](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md), puede programar una clase contenedora para dicho control.  En función de cómo pretenda manipular el control mediante programación, debe que escribir una o varias clases contenedoras del control.  
  
 Hay una clase contenedora para cada una de las coclases del archivo de la biblioteca de tipos del control \(.tlb\).  La clase contenedora del control debe tener el nombre del control con el prefijo C.  
  
 Para obtener más información acerca de la funcionalidad de las clases contenedoras, vea el modelo de objetos de la tecnología de base del control.  
  
 El uso de [CWnd::GetDlgItem](../Topic/CWnd::GetDlgItem.md) también requiere clases contenedoras, ya que el valor devuelto debe ser apropiado para la clase del control.  Por ejemplo:  
  
```  
CDBList* pDBList = 0;  
pDBList = static_cast<CDBList*>(GetDlgItem(IDC_DBLIST));  
```  
  
 Puede leer el archivo .idl generado para determinar las propiedades, los métodos y los eventos expuestos por un control, así como para ver directamente las declaraciones de métodos y funciones para descriptores de acceso.  Puede obtener información adicional del control mediante el [Visor de objetos OLE y COM](../../data/ado-rdo/using-the-ole-com-object-viewer.md).  
  
## Vea también  
 [Utilizar controles ActiveX](../../data/ado-rdo/using-activex-controls.md)   
 [Modificar el comportamiento de un control en tiempo de ejecución](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md)