---
title: "CComObjectRootEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComObjectRootEx"
  - "ATL::CComObjectRootEx<ThreadModel>"
  - "CComObjectRootEx"
  - "ATL::CComObjectRootEx"
  - "ATL.CComObjectRootEx<ThreadModel>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reference counting"
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObjectRootEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos a la administración del recuento de referencias de objeto ID para los objetos nonaggregated y agregados.  
  
## Sintaxis  
  
```  
  
      template<  
   class ThreadModel   
>  
class CComObjectRootEx : public CComObjectRootBase  
```  
  
#### Parámetros  
 `ThreadModel`  
 la clase cuyos métodos implementan el modelo de subprocesos deseado.  Puede elegir explícitamente el modelo de subprocesos estableciendo `ThreadModel` a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), a [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), o a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).  Puede aceptar el modelo predeterminado del subproceso servidor estableciendo `ThreadModel` a [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) o a [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md).  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[CComObjectRootEx](../Topic/CComObjectRootEx::CComObjectRootEx.md)|Constructor.|  
|[InternalAddRef](../Topic/CComObjectRootEx::InternalAddRef.md)|Incrementa el recuento de referencias para un objeto nonaggregated.|  
|[InternalRelease](../Topic/CComObjectRootEx::InternalRelease.md)|Decrementa para un objeto nonaggregated.|  
|[Bloquear](../Topic/CComObjectRootEx::Lock.md)|Si el modelo de subprocesos es multiproceso, obtiene la propiedad de un objeto de sección crítica.|  
|[Unlock](../Topic/CComObjectRootEx::Unlock.md)|Si el modelo de subprocesos es multiproceso, propiedad de un objeto de sección crítica.|  
  
### métodos de CComObjectRootBase  
  
|||  
|-|-|  
|[FinalConstruct](../Topic/CComObjectRootEx::FinalConstruct.md)|Reemplace en la clase para realizar cualquier inicialización requerida por el objeto.|  
|[FinalRelease](../Topic/CComObjectRootEx::FinalRelease.md)|Reemplace en la clase para realizar cualquier limpieza necesaria para el objeto.|  
|[OuterAddRef](../Topic/CComObjectRootEx::OuterAddRef.md)|Incrementa el recuento de referencias para un objeto agregado.|  
|[OuterQueryInterface](../Topic/CComObjectRootEx::OuterQueryInterface.md)|delegados a **IUnknown** externo de un objeto agregado.|  
|[OuterRelease](../Topic/CComObjectRootEx::OuterRelease.md)|Decrementa para un objeto agregado.|  
  
### Funciones de estático  
  
|||  
|-|-|  
|[InternalQueryInterface](../Topic/CComObjectRootEx::InternalQueryInterface.md)|delegados a **IUnknown** de un objeto nonaggregated.|  
|[ObjectMain](../Topic/CComObjectRootEx::ObjectMain.md)|Denominado durante la inicialización y la finalización de módulo para las clases derivadas enumeradas en el mapa del objeto.|  
  
### miembros de datos  
  
|||  
|-|-|  
|[m\_dwRef](../Topic/CComObjectRootEx::m_dwRef.md)|Con `m_pOuterUnknown`, parte de una combinación.  Se utiliza cuando el objeto no se agrega para contener el recuento de referencias de `AddRef` y de **Liberar**.|  
|[m\_pOuterUnknown](../Topic/CComObjectRootEx::m_pOuterUnknown.md)|Con `m_dwRef`, parte de una combinación.  Se utiliza cuando el objeto se agrega para contener un puntero al desconocido externo.|  
  
## Comentarios  
 administración del recuento de referencias de objeto de los identificadores de`CComObjectRootEx` para los objetos nonaggregated y agregados.  Contiene el recuento de referencias de objeto si el objeto no se suma, y mantiene el puntero a desconocido externo si se está agregando el objeto.  Para los objetos agregados, los métodos de `CComObjectRootEx` se pueden utilizar para controlar el error del objeto interno a la construcción, y proteger el objeto externo de eliminación cuando se publican interfaces internas o el objeto interno se elimina.  
  
 una clase que implementa un servidor COM debe heredar de `CComObjectRootEx` o de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).  
  
 Si la definición de clase especifica la macro de [DECLARE\_POLY\_AGGREGATABLE](../Topic/DECLARE_POLY_AGGREGATABLE.md) , ATL crea una instancia de **CComPolyObject \<CTheClass\>**  cuando se llama a **IClassFactory:: CreateInstance** .  Durante la creación, el valor desconocido externo se comprueba.  si es **NULL**, **IUnknown** se implementa para un objeto nonaggregated.  Si el hecho exterior no se **NULL**, **IUnknown** se implementa para un objeto agregado.  
  
 si la clase no especifica la macro de `DECLARE_POLY_AGGREGATABLE` , ATL crea una instancia de **CAggComObject \<CTheClass\>**  para los objetos agregados o una instancia de **CComObject \<CTheClass\>**  para los objetos nonaggregated.  
  
 La ventaja de utilizar `CComPolyObject` es que se evita tener `CComAggObject` y `CComObject` en el módulo para controlar los casos agregado y nonaggregated.  Los controladores de objeto de `CComPolyObject` ambos casos.  Por consiguiente, sólo una copia de vtable y una copia de las funciones existen en el módulo.  Si el vtable es grande, esto puede reducir considerablemente el tamaño del módulo.  Sin embargo, si el vtable es pequeño, mediante `CComPolyObject` pueden producir un tamaño ligeramente mayor de módulo porque no se optimiza para un objeto agregado o nonaggregated, al igual que `CComAggObject` y `CComObject`.  
  
 si se agrega el objeto, [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) es implementado por `CComAggObject` o `CComPolyObject`.  Estas clases delegan `QueryInterface`, `AddRef`, y las llamadas de **Liberar** a `OuterQueryInterface`, a `OuterAddRef`, y a `OuterRelease` de los entity\_CComObjectRootEx reenvíe al desconocido externo.  Normalmente, se reemplaza `CComObjectRootEx::FinalConstruct` en la clase para crear cualquier objeto agregado, y reemplaza `CComObjectRootEx::FinalRelease` para liberar los objetos agregados.  
  
 si el objeto no se agrega, **IUnknown** es implementado por `CComObject` o `CComPolyObject`.  En este caso, las llamadas a `QueryInterface`, `AddRef`, y **Liberar** se delegan en `InternalQueryInterface`, a `InternalAddRef`, y a `InternalRelease` de los entity\_CComObjectRootEx para realizar las operaciones reales.  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)