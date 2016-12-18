---
title: "IRowsetInfoImpl (Clase) | Microsoft Docs"
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
  - "ATL.IRowsetInfoImpl"
  - "IRowsetInfoImpl"
  - "ATL::IRowsetInfoImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetInfoImpl (clase)"
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetInfoImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación de la interfaz de [IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) .  
  
## Sintaxis  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
#### Parámetros  
 `T`  
 La clase, derivada de `IRowsetInfoImpl`.  
  
 `PropClass`  
 Una clase de propiedad definida por el usuario que toma como valor predeterminado la `T`.  
  
## Miembros  
  
### Métodos de interfaz  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)|Devuelve los valores actuales de todas las propiedades que el conjunto de filas admite.|  
|[GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)|Devuelve un puntero de interfaz al conjunto de filas al que el marcador aplica.|  
|[GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)|Devuelve un puntero de interfaz en el objeto \(comando o sesión\) que creó este conjunto de filas.|  
  
## Comentarios  
 Una interfaz de enlace en conjuntos de filas.  Esta clase implementa las propiedades del conjunto de filas mediante [mapa del conjunto de propiedades](../../data/oledb/begin-propset-map.md) definidas en la clase de comando.  Aunque la clase de conjunto de filas aparece para usar conjuntos de propiedades de clases de comandos, proporcionan el conjunto de filas con su propia copia de las propiedades en tiempo de ejecución, cuando crea un objeto de comando o de sesión.  
  
## Requisitos  
 **Header:** altdb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)