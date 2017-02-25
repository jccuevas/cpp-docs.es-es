---
title: "CDaoFieldInfo (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoFieldInfo (estructura)"
  - "DAO (objetos de acceso a datos), Fields (colección)"
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoFieldInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CDaoFieldInfo` contiene información sobre un objeto de campo definido para los objetos \(DAO\) de acceso a datos.  
  
## Sintaxis  
  
```  
  
      struct CDaoFieldInfo  
{  
   CString m_strName;           // Primary  
   short m_nType;               // Primary  
   long m_lSize;                // Primary  
   long m_lAttributes;          // Primary  
   short m_nOrdinalPosition;    // Secondary  
   BOOL m_bRequired;            // Secondary  
   BOOL m_bAllowZeroLength;     // Secondary  
   long m_lCollatingOrder;      // Secondary  
   CString m_strForeignName;    // Secondary  
   CString m_strSourceField;    // Secondary  
   CString m_strSourceTable;    // Secondary  
   CString m_strValidationRule; // All  
   CString m_strValidationText; // All  
   CString m_strDefaultValue;   // All  
};  
```  
  
#### Parámetros  
 `m_strName`  
 Nombres de forma única el objeto de campo.  Para obtener información detallada, vea el tema “propiedad Name” en la Ayuda de DAO.  
  
 `m_nType`  
 Un valor que indica el tipo de datos de campo.  Para obtener información detallada, vea el tema “propiedad de tipo” en la Ayuda de DAO.  El valor de esta propiedad puede ser:  
  
-   Sí\/No de**dbBoolean**, igual que **VERDADERO**\/**FALSE**  
  
-   byte de**dbByte**  
  
-   short de**dbInteger**  
  
-   **dbLong** Long  
  
-   moneda de**dbCurrency**; vea la clase MFC [COleCurrency](../../mfc/reference/colecurrency-class.md)  
  
-   **dbSingle** Single  
  
-   doble de**dbDouble**  
  
-   fecha y hora de**dbDate**; vea la clase MFC [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)  
  
-   texto de**dbText**; vea la clase MFC [CString](../../atl-mfc-shared/reference/cstringt-class.md)  
  
-   binario de**dbLongBinary**Long \(objeto OLE\); puede utilizar la clase MFC [CByteArray](../../mfc/reference/cbytearray-class.md) en lugar de la clase `CLongBinary` como `CByteArray` es más enriquecido y más fácil de utilizar.  
  
-   memorando de**dbMemo**; vea la clase MFC `CString`  
  
-   **dbGUID** un identificador único global y un identificador único universal utilizado con llamadas a procedimiento remoto.  Para obtener más información, vea el tema “propiedad de tipo” en la Ayuda de DAO.  
  
> [!NOTE]
>  No utilice tipos de datos de cadena para los datos binarios.  Esto hace que los datos al paso a través de la traducción de unicode\/ansi, lo que da como resultado sobrecarga mayor y posiblemente la traducción inesperada.  
  
 *m\_lSize*  
 Un valor que indica el tamaño máximo, en bytes, de un objeto de campo DAO que contiene el texto o el de tamaño fijo de un objeto de campo que contiene el texto o valores numéricos.  Para obtener información detallada, vea el tema “propiedad size” en la Ayuda de DAO.  Los tamaños pueden ser uno de los siguientes valores:  
  
|Tipo|Tamaño \(bytes\)|Descripción|  
|----------|----------------------|-----------------|  
|**dbBoolean**|1 byte|Sí\/No \(igual que True\/False\)|  
|**dbByte**|1|Byte|  
|**dbInteger**|2|Integer|  
|**dbLong**|4|Long|  
|**dbCurrency**|8|Moneda \([COleCurrency](../../mfc/reference/colecurrency-class.md)\)|  
|**dbSingle**|4|Single|  
|**dbDouble**|8|Double|  
|**dbDate**|8|Fecha y hora \([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)\)|  
|**dbText**|1 \- 255|Texto \([CString](../../atl-mfc-shared/reference/cstringt-class.md)\)|  
|**dbLongBinary**|0|Binario largo \(objeto OLE; [CByteArray](../../mfc/reference/cbytearray-class.md); en lugar de `CLongBinary`\)|  
|**dbMemo**|0|Memorando \([CString](../../atl-mfc-shared/reference/cstringt-class.md)\)|  
|**dbGUID**|16|Un identificador único global y un identificador único universal utilizado con llamadas a procedimiento remoto.|  
  
 `m_lAttributes`  
 Especifica las características de un objeto de campo contenido por un definición, un conjunto de registros, una tabla, o de índice.  El valor devuelto puede ser una suma de estas constantes, creada con C\+\+ bit a bit\- OR \(  **&#124;**\) operador:  
  
-   se corrige el tamaño de campo de**dbFixedField**\(valor predeterminado para los campos Numéricos de\).  
  
-   el tamaño de campo de**dbVariableField**The es variable \(campos de texto sólo\).  
  
-   el valor de campo de**dbAutoIncrField**The para los nuevos registros se incrementa automáticamente a un entero largo único que no se puede cambiar.  Solo se admite para las tablas de base de datos de Microsoft Jet.  
  
-   el valor de campo de**dbUpdatableField**The se puede cambiar.  
  
-   el campo de**dbDescending**La está ordenada de manera descendente \(z \)Pueda o 100 \- 0\) orden \(sólo se aplica a un objeto de campo en una colección de campos de un objeto de índice; en MFC, los propios objetos index se contienen en objetos de definición\).  Si omite esta constante, el campo se ordena de forma ascendente \(A \- z o 0 \- 100\) ordenada \(valor predeterminado\).  
  
 Al comprobar el valor de esta propiedad, puede utilizar el operador bit a bit \- AND de C\+\+ \(**&**\) para comprobar un atributo específico.  Al establecer varios atributos, puede combinarlos combinando las constantes adecuadas con bit a bit\- OR \(  **&#124;**\) operador.  Para obtener información detallada, vea el tema “propiedades de los atributos” en la Ayuda de DAO.  
  
 *m\_nOrdinalPosition*  
 Un valor que especifica el orden numérica en la que desea un campo representado por un objeto de campo DAO que se mostrará en relación con otros campos.  Puede establecer esta propiedad con [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md).  Para obtener información detallada, vea el tema “propiedades de OrdinalPosition” en la Ayuda de DAO.  
  
 `m_bRequired`  
 Indica si un objeto de campo de DAO requiere un valor no nulo.  Si esta propiedad es **VERDADERO**, el campo no permite un valor NULL.  Si es necesario se establece en **FALSE**, el campo puede contener valores nulos junto con los valores que cumplen las condiciones especificadas por los valores de propiedades de AllowZeroLength y de ValidationRule.  Para obtener información detallada, vea el tema “propiedad requeridas” en la Ayuda de DAO.  Puede establecer esta propiedad en un definición con [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md).  
  
 *m\_bAllowZeroLength*  
 Indica si una cadena vacía \(""\) es un valor válido de un objeto de campo DAO con un tipo de datos de texto o de memorando.  Si esta propiedad es **VERDADERO**, una cadena vacía es un valor válido.  Puede establecer esta propiedad en **FALSE** para asegurarse que no puede utilizar una cadena vacía para establecer el valor de un campo.  Para obtener información detallada, vea el tema “propiedades de AllowZeroLength” en la Ayuda de DAO.  Puede establecer esta propiedad en un definición con [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md).  
  
 `m_lCollatingOrder`  
 Especifica la secuencia del criterio de ordenación en el texto de la comparación de cadenas o la ordenación.  Para obtener detalles, vea el tema “personalizar de los valores del Registro de Windows para el acceso a datos” en la Ayuda de DAO.  Para obtener una lista de los posibles valores devueltos, vea el miembro de **m\_lCollatingOrder** de la estructura de [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) .  Puede establecer esta propiedad en un definición con [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md).  
  
 `m_strForeignName`  
 Un valor que, en una relación, especifica el nombre del objeto de campo de DAO en una tabla externa que corresponde a un campo de una tabla principal.  Para obtener información detallada, vea el tema “propiedades de ForeignName” en la Ayuda de DAO.  
  
 *m\_strSourceField*  
 Indica el nombre de campo que es el origen inicial de los datos para un objeto de campo DAO contenido por un definición, un conjunto de registros, o un objeto de tabla.  Esta propiedad indica el nombre de campo original asociado a un objeto de campo.  Por ejemplo, podría utilizar esta propiedad para determinar el origen inicial de los datos de un campo de consulta cuyo nombre no está relacionado con el nombre del campo de la tabla base.  Para obtener información detallada, vea el tema “SourceField, propiedades de SourceTable” en la Ayuda de DAO.  Puede establecer esta propiedad en un definición con [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md).  
  
 *m\_strSourceTable*  
 Indica el nombre de la tabla que es el origen inicial de los datos para un objeto de campo DAO contenido por un definición, un conjunto de registros, o un objeto de tabla.  Esta propiedad indica el nombre de tabla original asociado a un objeto de campo.  Por ejemplo, podría utilizar esta propiedad para determinar el origen inicial de los datos de un campo de consulta cuyo nombre no está relacionado con el nombre del campo de la tabla base.  Para obtener información detallada, vea el tema “SourceField, propiedades de SourceTable” en la Ayuda de DAO.  Puede establecer esta propiedad en un definición con [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md).  
  
 `m_strValidationRule`  
 Un valor que valida los datos en un campo mientras se cambia o se agrega a una tabla.  Para obtener información detallada, vea el tema “propiedades de ValidationRule” en la Ayuda de DAO.  Puede establecer esta propiedad en un definición con [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md).  
  
 Para obtener información relacionada sobre tabledefs, vea el miembro de **m\_strValidationRule** de la estructura de [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) .  
  
 `m_strValidationText`  
 Un valor que especifica el texto del mensaje que la aplicación muestra si el valor de un objeto de campo DAO no cumple la regla de validación especificada por el valor de las propiedades de ValidationRule.  Para obtener información detallada, vea el tema “propiedades de ValidationText” en la Ayuda de DAO.  Puede establecer esta propiedad en un definición con [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md).  
  
 *m\_strDefaultValue*  
 El valor predeterminado de un objeto de campo de DAO.  Cuando se crea un nuevo registro, el valor de la propiedad DefaultValue automáticamente se escribe como valor para el campo.  Para obtener información detallada, vea el tema “propiedad DefaultValue” en la Ayuda de DAO.  Puede establecer esta propiedad en un definición con [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md).  
  
## Comentarios  
 Las referencias a principal, a Secondary, y a Todo anterior indican cómo la información es devuelta por la función miembro de `GetFieldInfo` en las clases [CDaoTableDef](../Topic/CDaoTableDef::GetFieldInfo.md), [CDaoQueryDef](../Topic/CDaoQueryDef::GetFieldInfo.md), y [CDaoRecordset](../Topic/CDaoRecordset::GetFieldInfo.md).  
  
 Los objetos del campo no se representan mediante una clase MFC.  En su lugar, los objetos DAO que son la base de objetos MFC de las clases siguientes contienen colecciones de objetos de campo: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), y [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md).  El miembro de la fuente de estas clases funciona para tener acceso a algunos elementos individuales de la información de campo, o puede tener acceso de una vez a un objeto de `CDaoFieldInfo` llamando a la función miembro de `GetFieldInfo` de objeto contenedor.  
  
 Además de su uso para examinar las propiedades de objeto, puede utilizar `CDaoFieldInfo` para construir un parámetro de entrada para crear nuevos campos en un definición.  Opciones más sencillas están disponibles para esta tarea, pero si desea un control más preciso, puede utilizar la versión de [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md) que toma un parámetro de `CDaoFieldInfo` .  
  
 La información recuperada por la función miembro de `GetFieldInfo` \(de la clase que contiene el campo\) se almacena en una estructura de `CDaoFieldInfo` .  Llame a la función miembro de `GetFieldInfo` de objeto contenedor en cuya colección de campos se almacena el objeto de campo.  `CDaoFieldInfo` también define una función miembro de `Dump` en versiones de depuración.  Puede utilizar `Dump` para volcar el contenido de un objeto de `CDaoFieldInfo` .  
  
## Requisitos  
 **Header:** afxdao.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetFieldInfo](../Topic/CDaoTableDef::GetFieldInfo.md)   
 [CDaoRecordset::GetFieldInfo](../Topic/CDaoRecordset::GetFieldInfo.md)   
 [CDaoQueryDef::GetFieldInfo](../Topic/CDaoQueryDef::GetFieldInfo.md)