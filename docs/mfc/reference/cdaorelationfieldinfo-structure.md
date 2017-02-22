---
title: "CDaoRelationFieldInfo (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoRelationFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoRelationFieldInfo (estructura)"
  - "DAO (objetos de acceso a datos), colección de relaciones"
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoRelationFieldInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CDaoRelationFieldInfo` contiene información sobre un campo de una relación definida para los objetos \(DAO\) de acceso a datos.  
  
## Sintaxis  
  
```  
  
      struct CDaoRelationFieldInfo  
{  
   CString m_strName;           // Primary  
   CString m_strForeignName;    // Primary  
};  
```  
  
#### Parámetros  
 `m_strName`  
 El nombre del campo de la tabla principal de la relación.  
  
 `m_strForeignName`  
 El nombre del campo en la tabla externa de la relación.  
  
## Comentarios  
 Un objeto de relación de DAO especifica los campos de una tabla principal y los campos de una tabla externa que definen la relación.  Las referencias a primario en la definición de la estructura anterior indican cómo se devuelve en el miembro de `m_pFieldInfos` de un objeto de [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) obtenidos llamando a la función miembro de [GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md) de la clase `CDaoDatabase`.  
  
 Los objetos de la relación y los objetos del campo de la relación no se representan mediante una clase MFC.  En su lugar, los objetos DAO que son la base de los objetos MFC desde la clase [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) contienen una colección de objetos de la relación, denominada la colección de relaciones.  Cada objeto de relación, a su vez, contiene una colección de objetos del campo de la relación.  Cada objeto de campo de la relación relaciona un campo de la tabla principal a un campo en la tabla externa.  Conjuntamente, los objetos del campo de la relación se define un grupo de campos en cada tabla, que juntos definen la relación.  `CDaoDatabase` permite obtener acceso a objetos de la relación con un objeto de `CDaoRelationInfo` llamando al miembro de `GetRelationInfo` para funcionar.  El objeto de `CDaoRelationInfo` , a continuación, tiene un miembro de datos, `m_pFieldInfos`, que apunta a una matriz de los objetos de `CDaoRelationFieldInfo` .  
  
 Llame a la función miembro de [GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md) del objeto de `CDaoDatabase` que contiene en cuyas relaciones la colección se almacena el objeto de relación que le interesan.  A continuación obtenga acceso al miembro de `m_pFieldInfos` del objeto de [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) .  `CDaoRelationFieldInfo` también define una función miembro de `Dump` en versiones de depuración.  Puede utilizar `Dump` para volcar el contenido de un objeto de `CDaoRelationFieldInfo` .  
  
## Requisitos  
 **Header:** afxdao.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoRelationInfo \(Estructura\)](../../mfc/reference/cdaorelationinfo-structure.md)