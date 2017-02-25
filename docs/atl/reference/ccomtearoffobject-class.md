---
title: "CComTearOffObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComTearOffObject<Base>"
  - "ATL::CComTearOffObject"
  - "ATL.CComTearOffObject"
  - "ATL.CComTearOffObject<Base>"
  - "CComTearOffObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComTearOffObject class"
  - "tear-off interfaces"
  - "tear-off interfaces, ATL"
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CComTearOffObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa una interfaz de rasgón.  
  
## Sintaxis  
  
```  
  
      template<  
   class Base   
>  
class CComTearOffObject :  
   public Base  
```  
  
#### Parámetros  
 `Base`  
 La clase de rasgón, derivadas de `CComTearOffObjectBase` e interfaces desea que el objeto de rasgón admitir.  
  
 ATL implementa el rasga interfaces en dos fases — los métodos de `CComTearOffObjectBase` administran el recuento y `QueryInterface`de referencia, mientras que `CComTearOffObject` implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509).  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComTearOffObject::CComTearOffObject](../Topic/CComTearOffObject::CComTearOffObject.md)|el constructor.|  
|[CComTearOffObject::~CComTearOffObject](../Topic/CComTearOffObject::~CComTearOffObject.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComTearOffObject::AddRef](../Topic/CComTearOffObject::AddRef.md)|Incrementa el recuento de referencias de un objeto de `CComTearOffObject` .|  
|[CComTearOffObject::QueryInterface](../Topic/CComTearOffObject::QueryInterface.md)|Devuelve un puntero a la interfaz solicitada en la clase de rasgón o la clase propietaria.|  
|[CComTearOffObject::Release](../Topic/CComTearOffObject::Release.md)|Decrementa para un objeto de `CComTearOffObject` y destruir.|  
  
### métodos de CComTearOffObjectBase  
  
|||  
|-|-|  
|[CComTearOffObjectBase](../Topic/CComTearOffObject::CComTearOffObjectBase.md)|Constructor.|  
  
### miembros de datos de CComTearOffObjectBase  
  
|||  
|-|-|  
|[m\_pOwner](../Topic/CComTearOffObject::m_pOwner.md)|Un puntero a `CComObject` derivado de la clase propietaria.|  
  
## Comentarios  
 `CComTearOffObject` implementa una interfaz de rasgón como objeto independiente se cree instancias que cuando esa interfaz se consulta para.  Se elimina el rasgón cuando su recuento de referencia se convierte en cero.  Normalmente, se compila una interfaz de rasgón para una interfaz que se utilice raramente, ya que utilizar un rasgón guardar un puntero vtable en todas las instancias del objeto principal.  
  
 Debe derivar la clase que implementa el rasgón de `CComTearOffObjectBase` y de las interfaces desea que el objeto de rasgón admitir.  `CComTearOffObjectBase` templatized en la clase propietaria y el modelo de subprocesos.  La clase propietario es la clase del objeto para el que se implementa un rasgón.  Si no especifica un modelo de subprocesos, se utiliza el modelo predeterminado de subproceso.  
  
 Debe crear un mapa COM para la clase de rasgón.  Cuando ATL crea instancias del rasgón, creará **CComTearOffObject \<CTheTearOffClass\>**  o **CComCachedTearOffObject \<CTheTearOffClass\>** .  
  
 Por ejemplo, en el ejemplo BEEPER, la clase de `CBeeper2` es la clase de rasgón y la clase de `CBeeper` es la clase propietaria:  
  
 [!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/CPP/ccomtearoffobject-class_1.h)]  
  
## Jerarquía de herencia  
 `Base`  
  
 `CComTearOffObject`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComCachedTearOffObject Class](../../atl/reference/ccomcachedtearoffobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)