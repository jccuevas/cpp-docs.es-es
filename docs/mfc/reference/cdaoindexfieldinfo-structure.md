---
title: "CDaoIndexFieldInfo (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoIndexFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoIndexFieldInfo (estructura)"
  - "DAO (objetos de acceso a datos), Index Fields (colección)"
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CDaoIndexFieldInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CDaoIndexFieldInfo` contiene información sobre un objeto de campo de índice definido para los objetos \(DAO\) de acceso a datos.  
  
## Sintaxis  
  
```  
  
      struct CDaoIndexFieldInfo  
{  
   CString m_strName;          // Primary  
   BOOL m_bDescending;         // Primary  
};  
```  
  
#### Parámetros  
 `m_strName`  
 Nombres de forma única el objeto de campo de índice.  Para obtener información detallada, vea el tema “propiedad Name” en la Ayuda de DAO.  
  
 *el m\_bDescending*  
 Indica el orden de índice definido por el objeto de índice.  **VERDADERO** si el orden es descendente.  
  
## Comentarios  
 Un objeto de índice puede tener varios campos, indicando qué campos se indiza un definición \(o conjunto de registros basado en una tabla\) en.  Las referencias a anterior primario indican cómo se devuelve en el miembro de `m_pFieldInfos` de un objeto de [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) obtenidos llamando a la función miembro de `GetIndexInfo` de la clase [CDaoTableDef](../Topic/CDaoTableDef::GetIndexInfo.md) o [CDaoRecordset](../Topic/CDaoRecordset::GetIndexInfo.md).  
  
 Los objetos de índice y los objetos del campo de índice no se representan mediante una clase MFC.  En su lugar, los objetos DAO que son la base de los objetos MFC desde la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contienen una colección de objetos de índice, denominada la colección de índices.  Cada objeto de índice, a su vez, contiene una colección de objetos del campo.  El miembro de la fuente de estas clases funciona para tener acceso a elementos individuales de la información de índice, o puede tener acceso de una vez a un objeto de `CDaoIndexInfo` llamando a la función miembro de `GetIndexInfo` de objeto contenedor.  El objeto de `CDaoIndexInfo` , a continuación, tiene un miembro de datos, `m_pFieldInfos`, que apunta a una matriz de los objetos de `CDaoIndexFieldInfo` .  
  
 Llame a la función miembro de `GetIndexInfo` de definición o del objeto de conjunto de registros que contiene en cuyos índices la colección se almacena el objeto de índice que le interesan.  A continuación obtenga acceso al miembro de `m_pFieldInfos` del objeto de [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) .  La longitud de la matriz de `m_pFieldInfos` se almacena en `m_nFields`.  `CDaoIndexFieldInfo` también define una función miembro de `Dump` en versiones de depuración.  Puede utilizar `Dump` para volcar el contenido de un objeto de `CDaoIndexFieldInfo` .  
  
## Requisitos  
 **Header:** afxdao.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../Topic/CDaoTableDef::GetIndexInfo.md)   
 [CDaoRecordset::GetIndexInfo](../Topic/CDaoRecordset::GetIndexInfo.md)