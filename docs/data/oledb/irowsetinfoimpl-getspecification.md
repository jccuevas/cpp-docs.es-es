---
title: "IRowsetInfoImpl::GetSpecification | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetInfoImpl::GetSpecification"
  - "ATL.IRowsetInfoImpl.GetSpecification"
  - "IRowsetInfoImpl.GetSpecification"
  - "GetSpecification"
  - "ATL::IRowsetInfoImpl::GetSpecification"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetSpecification (método)"
ms.assetid: 8e14289d-9cca-4df7-a9e0-f4ef03c61e30
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetInfoImpl::GetSpecification
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un puntero de interfaz en el objeto \(comando o sesión\) que creó este conjunto de filas.  
  
## Sintaxis  
  
```  
  
      STDMETHOD ( GetSpecification )(  
   REFIID riid,  
   IUnknown** ppSpecification   
);  
```  
  
#### Parámetros  
 Vea [IRowsetInfo::GetSpecification](https://msdn.microsoft.com/en-us/library/ms716746.aspx) en *la referencia del*programador.  
  
## Comentarios  
 Utilice este método con [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md) para recuperar propiedades del objeto de origen de datos.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetInfoImpl \(Clase\)](../../data/oledb/irowsetinfoimpl-class.md)   
 [IRowsetInfoImpl::GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)   
 [IRowsetInfoImpl::GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)