---
title: "CDaoRelationInfo (Estructura) | Microsoft Docs"
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
  - "CDaoRelationInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoRelationInfo (estructura)"
  - "DAO (objetos de acceso a datos), colección de relaciones"
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoRelationInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CDaoRelationInfo` contiene información sobre una relación definida entre los campos de dos tablas en un objeto de [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .  
  
## Sintaxis  
  
```  
  
      struct CDaoRelationInfo  
{  
   CDaoRelationInfo( );                    // Constructor  
   CString m_strName;                      // Primary  
   CString m_strTable;                     // Primary  
   CString m_strForeignTable;              // Primary  
   long m_lAttributes;                     // Secondary  
   CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary  
   short m_nFields;                        // Secondary  
   // Below the // Implementation comment:  
   // Destructor, not otherwise documented  
};  
```  
  
#### Parámetros  
 `m_strName`  
 Nombres de forma única el objeto de relación.  Para obtener más información, vea el tema “propiedad Name” en la Ayuda de DAO.  
  
 *m\_strTable*  
 Nombres la tabla principal de la relación.  
  
 *m\_strForeignTable*  
 Nombres la tabla externa de la relación.  Una tabla externa es una tabla utilizada para contener las claves externas.  Normalmente, se utiliza una tabla externa para establecer o para exigir la integridad referencial.  La tabla externa es normalmente en muchos de los lados de una relación uno a varios.  Los ejemplos de tablas no nativas incluyen tablas que contienen los códigos de estados americanas o las provincias canadienses o los pedidos de los clientes.  
  
 `m_lAttributes`  
 Contiene información sobre el tipo de la relación.  El valor de este miembro puede ser cualquiera de los siguientes:  
  
-   **dbRelationUnique** Relación es uno por.  
  
-   **dbRelationDontEnforce** Relación no se aplica \(ninguna integridad referencial\).  
  
-   **dbRelationInherited** Relación existe en una base de datos no en ejecución que contiene las dos tablas asociadas.  
  
-   la relación de**dbRelationLeft**The es una combinación izquierda.  Una combinación externa izquierda incluye todos los registros de primeros \(izquierda\) de dos tablas, incluso si no hay valores coincidentes para los registros de la segunda tabla \(derecha\).  
  
-   la relación de**dbRelationRight**Z es right unión.  Una combinación externa derecha incluye todos los registros de segundos \(derecho\) de dos tablas, incluso si no hay valores coincidentes para los registros de la primera tabla \(izquierda\).  
  
-   las actualizaciones de**dbRelationUpdateCascade**ralentizan la cascada.  
  
-   **dbRelationDeleteCascade** Deletions cascada.  
  
 `m_pFieldInfos`  
 Un puntero a una matriz de estructuras de [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) .  La matriz contiene un objeto para cada campo de la relación.  El miembro de datos de `m_nFields` proporciona un recuento de los elementos de la matriz.  
  
 `m_nFields`  
 El número de objetos de `CDaoRelationFieldInfo` en el miembro de datos de `m_pFieldInfos` .  
  
## Comentarios  
 Las referencias a primario y a Secondary anteriores indican cómo la información es devuelta por la función miembro de [GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md) en la clase `CDaoDatabase`.  
  
 Los objetos de la relación no se representan mediante una clase MFC.  En su lugar, el objeto de DAO subyacente de un objeto de MFC de la clase de `CDaoDatabase` mantiene una colección de objetos de la relación: el miembro de `CDaoDatabase` funciona para tener acceso a algunos elementos individuales de la información de la relación, o puede tener acceso de una vez a un objeto de `CDaoRelationInfo` llamando a la función miembro de `GetRelationInfo` de objeto de base de datos que contiene.  
  
 La información recuperada por la función miembro de [CDaoDatabase::GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md) se almacena en una estructura de `CDaoRelationInfo` .  `CDaoRelationInfo` también define una función miembro de `Dump` en versiones de depuración.  Puede utilizar `Dump` para volcar el contenido de un objeto de `CDaoRelationInfo` .  
  
## Requisitos  
 **Header:** afxdao.h  
  
## Vea también  
 [CDaoRelationFieldInfo \(Estructura\)](../../mfc/reference/cdaorelationfieldinfo-structure.md)