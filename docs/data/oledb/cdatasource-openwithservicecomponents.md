---
title: "CDataSource::OpenWithServiceComponents | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataSource::OpenWithServiceComponents"
  - "OpenWithServiceComponents"
  - "CDataSource.OpenWithServiceComponents"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenWithServiceComponents (método)"
ms.assetid: 49c1d037-36ae-4fde-8e54-ced623abe1a9
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataSource::OpenWithServiceComponents
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Abre un objeto de origen de datos usando los componentes del servicio en oledb32.dll.  
  
## Sintaxis  
  
```  
  
        HRESULT OpenWithServiceComponents (  
   const CLSID clsid,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1   
);  
HRESULT OpenWithServiceComponents (  
   LPCSTR szProgID,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1   
);  
```  
  
#### Parámetros  
 `clsid`  
 \[in\] El **CLSID** del proveedor de datos.  
  
 `szProgID`  
 \[in\] Identificador de programa del proveedor de datos.  
  
 `pPropset`  
 \[in\] Puntero a una matriz de estructuras [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) que contiene las propiedades y los valores que se van a establecer.  Vea [Conjuntos de propiedades y grupos de propiedades](https://msdn.microsoft.com/en-us/library/ms713696.aspx) en la *Referencia del programador OLE DB* de [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  Si el objeto de origen de datos se inicializa, las propiedades tienen que pertenecer al grupo de propiedades Data Source.  Si la misma propiedad se especifica más de una vez en `pPropset`, el valor que se use será específico del proveedor.  Si `ulPropSets` es cero, este parámetro no se tiene en cuenta.  
  
 `ulPropSets`  
 \[in\] Número de estructuras [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) pasadas en el argumento *pPropSet*.  Si es cero, el proveedor omite `pPropset`.  
  
## Valor devuelto  
 Un `HRESULT` estándar.  
  
## Comentarios  
 Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio como la agrupación de recursos y la inscripción automática de transacciones, entre otras.  Para obtener más información, vea "Servicios OLE DB" en la Referencia del programador de OLE DB de [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataSource \(Clase\)](../../data/oledb/cdatasource-class.md)