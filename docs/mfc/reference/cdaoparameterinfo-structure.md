---
title: "CDaoParameterInfo (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoParameterInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoParameterInfo (estructura)"
  - "DAO (objetos de acceso a datos), Parameters (colección)"
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoParameterInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CDaoParameterInfo` contiene información sobre un objeto de parámetro definido para los objetos \(DAO\) de acceso a datos.  
  
## Sintaxis  
  
```  
  
      struct CDaoParameterInfo  
{  
   CString m_strName;       // Primary  
   short m_nType;           // Primary  
   ColeVariant m_varValue;  // Secondary  
};  
```  
  
#### Parámetros  
 `m_strName`  
 Nombres de forma única el objeto de parámetro.  Para obtener más información, vea el tema “propiedad Name” en la Ayuda de DAO.  
  
 `m_nType`  
 Un valor que indica el tipo de datos de un objeto de parámetro.  Para obtener una lista de valores posibles, vea el miembro de `m_nType` de la estructura de [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) .  Para obtener más información, vea el tema “propiedad de tipo” en la Ayuda de DAO.  
  
 *m\_varValue*  
 El valor del parámetro, almacenado en un objeto de [COleVariant](../../mfc/reference/colevariant-class.md) .  
  
## Comentarios  
 Las referencias a primario y a Secondary anteriores indican cómo la información es devuelta por la función miembro de [GetParameterInfo](../Topic/CDaoQueryDef::GetParameterInfo.md) en la clase `CDaoQueryDef`.  
  
 MFC no encapsula los objetos de parámetros de DAO en una clase.  Los objetos de tabla DAO que son la base de objetos MFC `CDaoQueryDef` almacenan parámetros en las colecciones de parámetros.  Para tener acceso a los objetos de parámetros en un objeto de [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) , llame a la función miembro de `GetParameterInfo` del objeto de tabla para un nombre de parámetro determinado o un índice en la colección de parámetros.  Puede utilizar la función miembro de [CDaoQueryDef::GetParameterCount](../Topic/CDaoQueryDef::GetParameterCount.md) junto con `GetParameterInfo` para recorrer en iteración la colección de parámetros.  
  
 La información recuperada por la función miembro de [CDaoQueryDef::GetParameterInfo](../Topic/CDaoQueryDef::GetParameterInfo.md) se almacena en una estructura de `CDaoParameterInfo` .  Llame a `GetParameterInfo` para el objeto de tabla en cuya colección de parámetros se almacena el objeto de parámetro.  
  
> [!NOTE]
>  Si desea obtener o para establecer el valor de un parámetro, use las funciones miembro de [GetParamValue](../Topic/CDaoRecordset::GetParamValue.md) y de [SetParamValue](../Topic/CDaoRecordset::SetParamValue.md) de la clase `CDaoRecordset`.  
  
 `CDaoParameterInfo` también define una función miembro de `Dump` en versiones de depuración.  Puede utilizar `Dump` para volcar el contenido de un objeto de `CDaoParameterInfo` .  
  
## Requisitos  
 **Header:** afxdao.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)