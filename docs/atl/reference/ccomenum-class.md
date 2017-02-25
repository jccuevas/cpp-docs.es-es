---
title: "CComEnum Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComEnum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComEnum class"
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CComEnum Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase define un objeto COM de enumerador basado en una matriz.  
  
## Sintaxis  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy,  
   class ThreadModel = CcomObjectThreadModel  
>  
class ATL_NO_VTABLE CComEnum :  
   public CComEnumImpl<Base, piid, T, Copy>,  
   public CComObjectRootEx< ThreadModel >  
```  
  
#### Parámetros  
 `Base`  
 Una interfaz COM de enumerador \(\).  
  
 `piid`  
 Un puntero al identificador de la interfaz de la interfaz del enumerador.  
  
 `T`  
 El tipo de elemento expuesto por la interfaz del enumerador.  
  
 `Copy`  
 [clase de directiva de copia](../../atl/atl-copy-policy-classes.md)homogéneo.  
  
 `ThreadModel`  
 el modelo de subprocesos de la clase.  Valor predeterminado de este parámetro al modelo de subproceso del objeto global utilizado en el proyecto.  
  
## Comentarios  
 `CComEnum` define un objeto COM de enumerador basado en una matriz.  Esta clase es análoga a [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) que implementa un enumerador basado en un contenedor de STL.  Los pasos típicos para utilizar esta clase se describen a continuación.  Para obtener más información, vea [Colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).  
  
## para utilizar esta clase:  
  
-   `typedef` una especialización de esta clase.  
  
-   Utilice `typedef` como argumento de plantilla en una especialización de `CComObject`.  
  
-   Cree una instancia de especialización de `CComObject` .  
  
-   Inicializa el objeto enumerator llamando a [CComEnumImpl:: Iniciar](../Topic/CComEnumImpl::Init.md).  
  
-   Devuelve la interfaz del enumerador al cliente.  
  
## Jerarquía de herencia  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)  
  
 `CComEnum`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Ejemplo  
 El código muestra siguiente proporciona una función reutilizable para crear e inicializar un objeto de enumerador.  
  
 [!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/CPP/ccomenum-class_1.h)]  
  
 Esta función de plantilla se puede utilizar para implementar la propiedad de `_NewEnum` de una interfaz de intercalación como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/CPP/ccomenum-class_2.h)]  
  
 Este código crea `typedef` para `CComEnum` que expone un vector de s para **VARIANT**a través de la interfaz de **IEnumVariant** .  La clase de **CVariantArrayCollection** especializada simplemente **CreateEnumerator** para trabajar con objetos de enumeradores de este tipo y pasa los argumentos necesarios.  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComObjectThreadModel](../Topic/CComObjectThreadModel.md)   
 [CComEnumImpl Class](../../atl/reference/ccomenumimpl-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)