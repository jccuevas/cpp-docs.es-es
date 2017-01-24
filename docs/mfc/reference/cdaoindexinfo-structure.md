---
title: "CDaoIndexInfo (Estructura) | Microsoft Docs"
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
  - "CDaoIndexInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoIndexInfo (estructura)"
  - "DAO (objetos de acceso a datos), colecciones indizadas"
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoIndexInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CDaoIndexInfo` contiene información sobre un objeto de índice definido para los objetos \(DAO\) de acceso a datos.  
  
## Sintaxis  
  
```  
  
      struct CDaoIndexInfo {  
   CDaoIndexInfo( );                   // Constructor  
   CString m_strName;                  // Primary  
   CDaoIndexFieldInfo* m_pFieldInfos;  // Primary  
   short m_nFields;                    // Primary  
   BOOL m_bPrimary;                    // Secondary  
   BOOL m_bUnique;                     // Secondary  
   BOOL m_bClustered;                  // Secondary  
   BOOL m_bIgnoreNulls;                // Secondary  
   BOOL m_bRequired;                   // Secondary  
   BOOL m_bForeign;                    // Secondary  
   long m_lDistinctCount;              // All  
  
   // Below the // Implementation comment:  
   // Destructor, not otherwise documented  
};   
```  
  
#### Parámetros  
 `m_strName`  
 Nombres de forma única el objeto de campo.  Para obtener información detallada, vea el tema “propiedad Name” en la Ayuda de DAO.  
  
 `m_pFieldInfos`  
 Puntero a una matriz de indicación de los objetos de [CDaoIndexFieldInfo](../../mfc/reference/cdaoindexfieldinfo-structure.md) qué campos de definición o de conjunto de registros son campos clave en un índice.  Cada objeto identifica un campo en el índice.  El orden predeterminado del índice es ascendente.  Un objeto de índice puede tener uno o más campos que representan las claves de índice para cada registro.  Pueden ser ascendente, entrega, o una combinación.  
  
 `m_nFields`  
 El número de campos almacenados en `m_pFieldInfos`.  
  
 *m\_bPrimary*  
 Si la propiedad primaria es **VERDADERO**, el objeto de índice representa un índice primario.  Un índice principal consta de uno o varios campos que identifican de forma exclusiva todos los registros de una tabla en un orden predefinido.  Como el campo de índice debe ser único, la propiedad Unique de objeto de índice también se establece en **VERDADERO** en DAO.  Si el índice principal consta de más de un campo, cada campo puede contener valores duplicados, pero cada combinación de valores de todos los campos indizados debe ser única.  Un índice primario se compone de una clave para la tabla y normalmente contiene los mismos campos que la clave principal.  
  
 Cuando se establece una clave principal para una tabla, la clave principal definen como índice principal para la tabla.  Para obtener más información, vea los temas “propiedad primaria” y “propiedad Unique” en la Ayuda de DAO.  
  
> [!NOTE]
>  Puede haber, como máximo, un índice principal de una tabla.  
  
 *m\_bUnique*  
 Indica si un objeto de índice representa un índice único para una tabla.  Si esta propiedad es **VERDADERO**, el objeto de índice representa un índice que sea único.  Un índice único consta de uno o más campos que organicen lógicamente todos los registros de una tabla en un orden único, predefinido.  Si el índice está compuesto de un campo, los valores de que el campo debe ser único para la tabla completa.  Si el índice está formada por más de un campo, cada campo puede contener valores duplicados, pero cada combinación de valores de todos los campos indizados debe ser única.  
  
 Si el UNIQUE y las propiedades principales de un objeto de índice se establecen en **VERDADERO**, el índice es único y primario: Identifica todos los registros de la tabla en un orden predefinido, lógico.  Si la propiedad primaria se establece en **FALSE**, el índice es un índice secundario.  Los índices secundarios \(tanto nonkey\) organizan lógicamente los registros en un orden predefinido sin el servicio como identificador para los registros de la tabla.  
  
 Para obtener más información, vea los temas “propiedad primaria” y “propiedad Unique” en la Ayuda de DAO.  
  
 *m\_bClustered*  
 Indica si un objeto de índice representa un índice clúster de una tabla.  Si esta propiedad es **VERDADERO**, el objeto de índice representa un índice clúster; si no, no.  Un índice clúster consta de uno o más campos nonkey que, en conjunto, organicen todos los registros de una tabla en un orden predefinido.  Con un índice clúster, los datos de la tabla se almacena literalmente en el orden especificado por el índice clúster.  Un índice agrupado proporciona acceso eficaz en una tabla.  Para obtener más información, vea el tema “agrupados la propiedad” en la Ayuda de DAO.  
  
> [!NOTE]
>  La propiedad en clúster se omite para las bases de datos que utilizan el motor de base de datos Microsoft Jet porque el motor de base de datos de Jet no admite índices agrupados.  
  
 *m\_bIgnoreNulls*  
 Indica si hay entradas de índice para los registros que tienen valores NULL en los campos de índice.  Si esta propiedad es **VERDADERO**, los campos con valores NULL no tienen una entrada de índice.  Para crear buscar los registros utilizando un campo más rápidamente, puede definir un índice para el campo.  Si permite las entradas de Null en un campo indizado y espera que muchas de las entradas sean Null, puede establecer la propiedad de IgnoreNulls para el objeto de índice a **VERDADERO** para reducir la cantidad de espacio de almacenamiento que el índice utiliza.  El valor de las propiedades de IgnoreNulls y el valor de propiedades requeridas unidos determinan si un registro con un valor de índice de Null tiene una entrada de índice, como se muestra en la tabla siguiente.  
  
|IgnoreNulls|Necesario|NULL en el campo de índice|  
|-----------------|---------------|--------------------------------|  
|True|False|Valor NULL permitido; ninguna entrada de índice agregada.|  
|False|False|Valor NULL permitido; entrada de índice agregada.|  
|True o False|True|Valor NULL no permitida; ninguna entrada de índice agregada.|  
  
 Para obtener más información, vea el tema “propiedades de IgnoreNulls” en la Ayuda de DAO.  
  
 `m_bRequired`  
 Indica si un objeto de índice de DAO requiere un valor no nulo.  Si esta propiedad es **VERDADERO**, el objeto de índice no permite un valor NULL.  Para obtener más información, vea el tema “propiedad requeridas” en la Ayuda de DAO.  
  
> [!TIP]
>  Cuando puede establecer esta propiedad en un objeto de índice de DAO o un objeto de campo \(contenido por un definición, un conjunto de registros, o un objeto de tabla\), configúrelo para el objeto de campo.  La validez del valor de propiedad de un objeto de campo se comprueba antes de un objeto de índice.  
  
 *m\_bForeign*  
 Indica si un objeto de índice representa una clave externa en una tabla.  Si esta propiedad es **VERDADERO**, el índice representa una clave externa en una tabla.  Una clave externa consta de uno o más campos de una tabla externa que identifican de forma única una fila de una tabla principal.  El motor de base de datos Microsoft Jet crea un objeto de índice para la tabla externa y establezca la propiedad de Foreign al crear una relación que se aplique integridad referencial.  Para obtener más información, vea el tema “propiedades de Foreign” en la Ayuda de DAO.  
  
 *m\_lDistinctCount*  
 Indica el número de valores únicos para el objeto de índice que se incluyen en la tabla asociada.  Compruebe la propiedad de DistinctCount para determinar el número de valores únicos, o de teclas, en un índice.  Cualquier tecla se cuenta una sola vez, aunque puede haber varias apariciones de ese valor si el índice permite valores duplicados.  Esta información es útil en aplicaciones que intentan optimizar acceso a datos evalúa la información de índice.  El número de valores únicos también se conoce como la cardinalidad de un objeto de índice.  La propiedad de DistinctCount no reflejará siempre el número real de teclas en un momento determinado.  Por ejemplo, un cambio producido por una reversión de la transacción no se reflejará inmediatamente en la propiedad de DistinctCount.  Para obtener más información, vea el tema “propiedades de DistinctCount” en la Ayuda de DAO.  
  
## Comentarios  
 Las referencias a principal, a Secondary, y a Todo anterior indican cómo la información es devuelta por la función miembro de `GetIndexInfo` en las clases [CDaoTableDef](../Topic/CDaoTableDef::GetIndexInfo.md) y [CDaoRecordset](../Topic/CDaoRecordset::GetIndexInfo.md).  
  
 Los objetos de índice no se representan mediante una clase MFC.  En su lugar, los objetos DAO que son la base de los objetos MFC desde la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contienen una colección de objetos de índice, denominada la colección de índices.  El miembro de la fuente de estas clases funciona para tener acceso a elementos individuales de la información de índice, o puede tener acceso de una vez a un objeto de `CDaoIndexInfo` llamando a la función miembro de `GetIndexInfo` de objeto contenedor.  
  
 `CDaoIndexInfo` tiene un constructor y el destructor para asignar y desasignar correctamente la información de campo de índice en `m_pFieldInfos`.  
  
 La información recuperada por la función miembro de `GetIndexInfo` de un objeto de definición se almacena en una estructura de `CDaoIndexInfo` .  Llame a la función miembro de `GetIndexInfo` del objeto de definición que contiene en cuya colección de índices se almacena el objeto de índice.  `CDaoIndexInfo` también define una función miembro de `Dump` en versiones de depuración.  Puede utilizar `Dump` para volcar el contenido de un objeto de `CDaoIndexInfo` .  
  
## Requisitos  
 **Header:** afxdao.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../Topic/CDaoTableDef::GetIndexInfo.md)