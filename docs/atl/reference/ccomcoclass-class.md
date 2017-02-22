---
title: "CComCoClass Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComCoClass"
  - "ATL.CComCoClass"
  - "ATL::CComCoClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregation [C++], aggregation models"
  - "CComCoClass class"
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComCoClass Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para crear instancias de una clase, y obtener sus propiedades.  
  
## Sintaxis  
  
```  
  
      template<  
   class T,  
   const CLSID* pclsid = &CLSID_NULL  
>  
class CComCoClass  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `CComCoClass`.  
  
 *pclsid*  
 Un puntero al CLSID del objeto.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCoClass::CreateInstance](../Topic/CComCoClass::CreateInstance.md)|\(Estático\) crea una instancia de la clase y las consultas de una interfaz.|  
|[CComCoClass::Error](../Topic/CComCoClass::Error.md)|\(Estático\) devuelve información de error completa al cliente.|  
|[CComCoClass::GetObjectCLSID](../Topic/CComCoClass::GetObjectCLSID.md)|\(Estático\) devuelve el identificador de clase del objeto.|  
|[CComCoClass::GetObjectDescription](../Topic/CComCoClass::GetObjectDescription.md)|\(Estático\) reemplace para devolver la descripción del objeto.|  
  
## Comentarios  
 `CComCoClass` proporciona métodos para recuperar el CLSID de un objeto, establecer la información de error, y crear instancias de la clase.  cualquier clase registrada en [mapa de objetos](http://msdn.microsoft.com/es-es/b57619cc-534f-4b8f-bfd4-0c12f937202f) debe ser derivada de `CComCoClass`.  
  
 `CComCoClass` también define el modelo predeterminado de generador y la agregación de clase del objeto.  `CComCoClass` usa las dos macros siguientes:  
  
-   [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md) declara el generador de la clase se [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).  
  
-   [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md) declara que el objeto puede agregarse.  
  
 Puede reemplazar cualquiera de estos valores predeterminados especificando otra macro en la definición de clase.  Por ejemplo, para utilizar [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) en lugar de `CComClassFactory`, especifique la macro de [DECLARE\_ CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) :  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/CPP/ccomcoclass-class_1.h)]  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)