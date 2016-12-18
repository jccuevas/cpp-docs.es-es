---
title: "IAccessorImpl (Clase) | Microsoft Docs"
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
  - "IAccessorImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAccessorImpl (clase)"
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAccessorImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación de la interfaz de [IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) .  
  
## Sintaxis  
  
```  
template <  
   class T,   
   class BindType = ATLBINDINGS,   
   class BindingVector = CAtlMap <   
      HACCESSOR hAccessor,   
      BindType* pBindingsStructure   
   >   
>  
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>  
```  
  
#### Parámetros  
 `T`  
 La clase de conjunto de filas o del objeto de comando.  
  
 `BindType`  
 Unidad de almacenamiento para la información de enlace.  El valor predeterminado es la estructura de **ATLBINDINGS** \(vea atldb.h\).  
  
 `BindingVector`  
 Unidad de almacenamiento para la información de columna.  El valor predeterminado es [CAtlMap](../../atl/reference/catlmap-class.md) donde es un valor el elemento clave de **HACCESSOR** y el elemento del valor es un puntero a una estructura de `BindType` .  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)|Constructor.|  
  
### Métodos de interfaz  
  
|||  
|-|-|  
|[AddRefAccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)|Agrega un contador de referencias a un descriptor de acceso existente.|  
|[CreateAccessor](../../data/oledb/iaccessorimpl-createaccessor.md)|Crea un descriptor de acceso a partir de un conjunto de enlaces.|  
|[GetBindings](../../data/oledb/iaccessorimpl-getbindings.md)|Devuelve los enlaces de un descriptor de acceso.|  
|[ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)|Libera un descriptor de acceso.|  
  
## Comentarios  
 Esto es obligatorio en conjuntos de filas y los comandos.  OLE DB requiere los proveedores implementar **HACCESSOR**, que es una etiqueta a una matriz de estructuras de [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) .  S para**HACCESSOR**proporcionada por `IAccessorImpl` es direcciones de estructuras de `BindType` .  De forma predeterminada, `BindType` se define como **ATLBINDINGS** en la definición de plantilla de `IAccessorImpl` .  `BindType` proporciona un mecanismo utilizado por `IAccessorImpl` para realizar el seguimiento del número de elementos de la matriz de **DBBINDING** junto con un recuento de referencia y los indicadores de descriptor de acceso.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)