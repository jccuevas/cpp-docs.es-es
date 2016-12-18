---
title: "CDaoDatabaseInfo (Estructura) | Microsoft Docs"
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
  - "CDaoDatabaseInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoDatabaseInfo (estructura)"
  - "DAO (objetos de acceso a datos), colección de bases de datos"
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoDatabaseInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CDaoDatabaseInfo` contiene información sobre un objeto de base de datos definido para los objetos \(DAO\) de acceso a datos.  
  
## Sintaxis  
  
```  
  
      struct CDaoDatabaseInfo  
{  
   CString m_strName;       // Primary  
   BOOL m_bUpdatable;       // Primary  
   BOOL m_bTransactions;    // Primary  
   CString m_strVersion;    // Secondary  
   long m_lCollatingOrder;  // Secondary  
   short m_nQueryTimeout;   // Secondary  
   CString m_strConnect;    // All  
};  
```  
  
#### Parámetros  
 `m_strName`  
 Nombres de forma única el objeto de base de datos.  Para recuperar directamente esta propiedad, llame a [CDaoDatabase::GetName](../Topic/CDaoDatabase::GetName.md).  Para obtener información detallada, vea el tema “propiedad Name” en la Ayuda de DAO.  
  
 `m_bUpdatable`  
 Indica si se pueden realizar en la base de datos.  Para recuperar directamente esta propiedad, llame a [CDaoDatabase::CanUpdate](../Topic/CDaoDatabase::CanUpdate.md).  Para obtener información detallada, vea el tema “propiedades de Actualizable” en la Ayuda de DAO.  
  
 *m\_bTransactions*  
 Indica si un origen de datos admite transacciones — la grabación de una serie de cambios que puedan más adelante ser posteriores rodado \(cancelan\) o de confianza \(guardado\).  Si una base de datos se basa en el motor de base de datos Microsoft Jet, la propiedad de las transacciones es distinto de cero y puede utilizar transacciones.  Otros motores de base de datos pueden no admitir transacciones.  Para recuperar directamente esta propiedad, llame a [CDaoDatabase::CanTransact](../Topic/CDaoDatabase::CanTransact.md).  Para obtener información detallada, vea el tema “propiedades de transacciones” en la Ayuda de DAO.  
  
 *m\_strVersion*  
 Indica la versión del motor de base de datos Microsoft Jet.  Para recuperar el valor de esta propiedad directamente, llame a la función miembro de [GetVersion](../Topic/CDaoDatabase::GetVersion.md) del objeto de base de datos.  Para obtener información detallada, vea el tema “propiedad version” en la Ayuda de DAO.  
  
 `m_lCollatingOrder`  
 Especifica la secuencia del criterio de ordenación en el texto de la comparación de cadenas o la ordenación.  Los posibles valores incluyen:  
  
-   uso de**dbSortGeneral**el criterio de ordenación General \(inglés, francés, alemán, portugués, italiano, español y de Modern\).  
  
-   uso de**dbSortArabic**el orden árabe.  
  
-   uso de**dbSortCyrillic**el criterio de ordenación ruso.  
  
-   uso de**dbSortCzech**el criterio de ordenación checo.  
  
-   uso de**dbSortDutch** el criterio de ordenación neerlandés.  
  
-   uso de**dbSortGreek**el criterio de ordenación griego.  
  
-   uso de**dbSortHebrew**el orden hebreo.  
  
-   uso de**dbSortHungarian**el criterio de ordenación húngaro.  
  
-   uso de**dbSortIcelandic**el criterio de ordenación islandés.  
  
-   uso de**dbSortNorwdan**el criterio de ordenación noruego o danés.  
  
-   uso de**dbSortPDXIntl**el criterio de ordenación Paradox Internacional.  
  
-   uso de**dbSortPDXNor**criterio de ordenación noruego o danés de Paradox.  
  
-   uso de**dbSortPDXSwe**criterio de ordenación sueco o finés de Paradox.  
  
-   uso de**dbSortPolish**el criterio de ordenación polaco.  
  
-   uso de**dbSortSpanish**el criterio de ordenación español.  
  
-   uso de**dbSortSwedFin**el criterio de ordenación sueco o finés.  
  
-   uso de**dbSortTurkish**el criterio de ordenación turco.  
  
-   el criterio de ordenación de**dbSortUndefined**Z es indefinido o desconocido.  
  
 Para obtener más información, vea el tema “personalizar de los valores del Registro de Windows para el acceso a datos” en la Ayuda de DAO.  
  
 *m\_nQueryTimeout*  
 El número de segundos que el motor de base de datos Microsoft Jet espera antes de que un error de tiempo de espera aparece cuando una consulta se ejecuta en una base de datos ODBC.  El valor de tiempo de espera predeterminado es de 60 segundos.  Cuando QueryTimeout se establece en 0, ningún tiempo de espera aparece; esto puede hacer que el programa deje de responder.  Para recuperar el valor de esta propiedad directamente, llame a la función miembro de [GetQueryTimeout](../Topic/CDaoDatabase::GetQueryTimeout.md) del objeto de base de datos.  Para obtener información detallada, vea el tema “propiedades de QueryTimeout” en la Ayuda de DAO.  
  
 `m_strConnect`  
 Proporciona información sobre el origen de una base de datos abierto.  Para obtener información sobre las cadenas se conectan, y para obtener información sobre cómo recuperar el valor de esta propiedad directamente, vea la función miembro de [CDaoDatabase::GetConnect](../Topic/CDaoDatabase::GetConnect.md) trabajar.  Para obtener más información, vea el tema “propiedad conectar” en la Ayuda de DAO.  
  
## Comentarios  
 La base de datos es un objeto de DAO subyacente de un objeto MFC desde la clase [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md).  Las referencias a principal, a Secondary, y a Todo anterior indican cómo la información es devuelta por la función miembro de [CDaoWorkspace::GetDatabaseInfo](../Topic/CDaoWorkspace::GetDatabaseInfo.md) .  
  
 La información recuperada por la función miembro de [CDaoWorkspace::GetDatabaseInfo](../Topic/CDaoWorkspace::GetDatabaseInfo.md) se almacena en una estructura de `CDaoDatabaseInfo` .  Llame a `GetDatabaseInfo` para el objeto de `CDaoWorkspace` en cuya colección de bases de datos se almacena el objeto de base de datos.  `CDaoDatabaseInfo` también define una función miembro de `Dump` en versiones de depuración.  Puede utilizar `Dump` para volcar el contenido de un objeto de `CDaoDatabaseInfo` .  
  
## Requisitos  
 **Header:** afxdao.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoWorkspace::GetDatabaseCount](../Topic/CDaoWorkspace::GetDatabaseCount.md)