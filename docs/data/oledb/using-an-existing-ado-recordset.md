---
title: "Utilizar un conjunto de registros ADO existente | Microsoft Docs"
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
  - "conjuntos de registros ADO [C++]"
  - "plantillas de consumidor OLE DB, conjuntos de registros ADO"
  - "conjuntos de registros [C++], utilizar en OLE DB"
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar un conjunto de registros ADO existente
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para combinar plantillas de consumidor OLE DB con la tecnología Active Data Objects \(ADO\), use ADO para abrir un conjunto de registros \(equivalente al conjunto de filas de las plantillas de consumidor OLE DB\).  Cuando tenga un conjunto de registros, haga lo siguiente para conectar con un conjunto de filas OLE DB:  
  
1.  Llame a `QueryInterface` para los punteros `IRowset` e `IAccessor`.  
  
    ```  
    IRowset* lpRowset = NULL;  
    IAccessor* lpAccessor = NULL;  
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);  
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);  
    ```  
  
    > [!NOTE]
    >  *lpUnk* señala al objeto **IUnknown** del conjunto de registros ADO.  
  
2.  Asocie el descriptor de acceso y el conjunto de filas a sus clases correspondientes de plantillas de consumidor OLE DB.  
  
    ```  
    CRowset rs;  
    CAccessor accessor;  
  
    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor  
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>  
    rs.SetAccessor(accessor);  
    ```  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)