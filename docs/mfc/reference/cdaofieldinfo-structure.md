---
title: CDaoFieldInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 15db0c56480dfefb9fc8806c08596e37c7d38eb2
ms.lasthandoff: 02/24/2017

---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo (Estructura)
El `CDaoFieldInfo` estructura contiene información sobre un objeto de campo definido para objetos de acceso a datos (DAO).  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `m_strName`  
 Nombres de forma exclusiva el objeto de campo. Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
 `m_nType`  
 Un valor que indica el tipo de datos del campo. Para obtener más información, vea el tema "Tipo de propiedad" en la Ayuda de DAO. El valor de esta propiedad puede ser uno de los siguientes:  
  
- **dbBoolean** Sí o No, igual que **TRUE**/**FALSE**  
  
- **dbByte** bytes  
  
- **dbInteger** corto  
  
- **dbLong** largo  
  
- **dbCurrency** moneda; vea clase MFC [OLECurrency.](../../mfc/reference/colecurrency-class.md)  
  
- **dbSingle** único  
  
- **dbDouble** dobles  
  
- **dbDate** de fecha y hora; vea clase MFC [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)  
  
- **dbText** texto; Vea clase MFC [CString](../../atl-mfc-shared/reference/cstringt-class.md)  
  
- **dbLongBinary** binario largo (objeto OLE); puede usar la clase MFC [CByteArray](../../mfc/reference/cbytearray-class.md) en lugar de la clase `CLongBinary` como `CByteArray` es más rico y más fácil de usar.  
  
- **dbMemo** memorando; vea MFC (clase)`CString`  
  
- **dbGUID** un identificador único global identificador/universalmente único utilizado con llamadas a procedimiento remoto. Para obtener más información, vea el tema "Tipo de propiedad" en la Ayuda de DAO.  
  
> [!NOTE]
>  No utilice tipos de datos string para datos binarios. Esto hace que los datos pasar a través de la capa de conversión Unicode/ANSI, lo que resulta en una mayor sobrecarga y posiblemente inesperada de traducción.  
  
 *m_lSize*  
 Un valor que indica el tamaño máximo, en bytes, de un objeto de campo DAO que contiene el texto o el tamaño de un objeto de campo que contiene valores numéricos o de texto fijo. Para obtener más información, vea el tema "Propiedad de tamaño" en la Ayuda de DAO. Tamaños pueden ser uno de los siguientes valores:  
  
|Tipo|Tamaño (bytes)|Descripción|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 byte|Sí/No (igual como verdadero/falso)|  
|**dbByte**|1|Byte|  
|**dbInteger**|2|Integer|  
|**dbLong**|4|Long|  
|**dbCurrency**|8|Moneda ([COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|Single|  
|**dbDouble**|8|Doble|  
|**dbDate**|8|Fecha y hora ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 - 255|Texto ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|Binarios largos (objeto OLE; [CByteArray](../../mfc/reference/cbytearray-class.md); utilice en lugar de `CLongBinary`)|  
|**dbMemo**|0|Memorando ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbGUID**|16|Un identificador único global identificador/universalmente único se utiliza con llamadas a procedimiento remoto.|  
  
 `m_lAttributes`  
 Especifica las características de un objeto de campo contenida una definición de tabla, recordset, querydef o el objeto de índice. El valor devuelto puede ser la suma de estas constantes, creadas con C++ OR bit a bit (**|**) (operador):  
  
- **dbFixedField** el tamaño del campo es fijo (valor predeterminado para los campos numéricos).  
  
- **dbVariableField** el tamaño del campo es variable (sólo campos de texto).  
  
- **dbAutoIncrField** el valor del campo para nuevos registros se incrementa automáticamente en un entero largo único que no se puede cambiar. Solo se admite para las tablas de base de datos Microsoft Jet.  
  
- **dbUpdatableField** se puede cambiar el valor del campo.  
  
- **dbDescending** el campo se ordena en orden descendente (Z - A o de 0 a 100) pedido (sólo se aplica a un objeto field en una colección de campos de un objeto de índice; en MFC, ellos mismos objetos están contenidos en objetos de definición de tabla de índice). Si se omite esta constante, el campo se ordena en orden ascendente (A - Z o 0 - 100) pedido (valor predeterminado).  
  
 Al comprobar la configuración de esta propiedad, puede usar C++ bit a bit- y operador (**&**) para probar si un atributo específico. Al establecer varios atributos, se pueden combinar mediante la combinación de las constantes adecuadas con la operación bit a bit OR (**|**) (operador). Para obtener más información, vea el tema "Propiedad Attributes" en la Ayuda de DAO.  
  
 *m_nOrdinalPosition*  
 Un valor que especifica el orden numérico en el que desea que un campo representado por un objeto de campo DAO que se mostrará en relación con otros campos. Puede establecer esta propiedad con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Para obtener más información, vea el tema "Propiedad OrdinalPosition" en la Ayuda de DAO.  
  
 `m_bRequired`  
 Indica si un objeto de campo DAO requiere un valor distinto de Null. Si esta propiedad es **TRUE**, el campo no permite un valor Null. Si se establece en requiere **FALSE**, el campo puede contener valores Null, así como valores que cumplan las condiciones especificadas por los valores de propiedad AllowZeroLength y ValidationRule. Para obtener más información, vea el tema "Propiedad necesaria" en la Ayuda de DAO. Puede establecer esta propiedad para un objeto tabledef con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 *m_bAllowZeroLength*  
 Indica si una cadena vacía ("") es un valor válido de un objeto de campo DAO con un tipo de datos texto o Memo. Si esta propiedad es **TRUE**, una cadena vacía es un valor válido. Puede establecer esta propiedad en **FALSE** para garantizar que no se puede usar una cadena vacía para establecer el valor de un campo. Para obtener más información, vea el tema "Propiedad Permitir longitud cero" en la Ayuda de DAO. Puede establecer esta propiedad para un objeto tabledef con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 `m_lCollatingOrder`  
 Especifica la secuencia del criterio de ordenación en texto para comparación de cadenas o de ordenación. Para obtener más información, vea el tema "Personalización de Windows del registro configuración de acceso a datos" en la Ayuda de DAO. Para obtener una lista de los posibles valores devueltos, consulte la **m_lCollatingOrder** miembro de la [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) estructura. Puede establecer esta propiedad para un objeto tabledef con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 `m_strForeignName`  
 Un valor que, en una relación, especifica el nombre del objeto DAO campo en una tabla externa que corresponde a un campo de una tabla principal. Para obtener más información, vea el tema "Propiedad ForeignName" en la Ayuda de DAO.  
  
 *m_strSourceField*  
 Indica el nombre del campo que es el origen de los datos de un objeto de campo DAO contenido por objeto querydef, recordset o tabledef. Esta propiedad indica el nombre del campo original asociado a un objeto de campo. Por ejemplo, podría utilizar esta propiedad para determinar el origen inicial de los datos en un campo de consulta cuyo nombre no está relacionado con el nombre del campo en la tabla subyacente. Para obtener más información, vea el tema "SourceField y SourceTable propiedades" en la Ayuda de DAO. Puede establecer esta propiedad para un objeto tabledef con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 *m_strSourceTable*  
 Indica el nombre de la tabla que es el origen de los datos de un objeto de campo DAO contenido por objeto querydef, recordset o tabledef. Esta propiedad indica el nombre de tabla original asociado a un objeto de campo. Por ejemplo, podría utilizar esta propiedad para determinar el origen inicial de los datos en un campo de consulta cuyo nombre no está relacionado con el nombre del campo en la tabla subyacente. Para obtener más información, vea el tema "SourceField y SourceTable propiedades" en la Ayuda de DAO. Puede establecer esta propiedad para un objeto tabledef con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 `m_strValidationRule`  
 Un valor que valida los datos de un campo cuando se cambia o se agrega a una tabla. Para obtener más información, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO. Puede establecer esta propiedad para un objeto tabledef con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 Para obtener información relacionada sobre definiciones de tabla, consulte el **m_strValidationRule** miembro de la [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) estructura.  
  
 `m_strValidationText`  
 Un valor que especifica el texto del mensaje que su aplicación muestra si el valor de un objeto de campo DAO no satisface la regla de validación especificada por el valor de la propiedad ValidationRule. Para obtener más información, vea el tema "Propiedad texto de validación" en la Ayuda de DAO. Puede establecer esta propiedad para un objeto tabledef con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 *m_strDefaultValue*  
 El valor predeterminado de un objeto de campo DAO. Cuando se crea un nuevo registro, la propiedad DefaultValue automáticamente se escribe como el valor para el campo. Para obtener más información, vea el tema "Propiedad DefaultValue" en la Ayuda de DAO. Puede establecer esta propiedad para un objeto tabledef con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
## <a name="remarks"></a>Comentarios  
 Las referencias al principal, secundaria y todo lo anterior indican cómo devuelve la información de la `GetFieldInfo` función miembro en clases [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo), y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).  
  
 Objetos de campo no se representan mediante una clase MFC. En su lugar, los objetos DAO de MFC objetos de las siguientes clases subyacentes contienen colecciones de objetos de campo: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), y [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Estas clases proporcionan funciones de miembro para tener acceso a algunos elementos individuales de la información de campo, o puede tener acceso a ellos a la vez con un `CDaoFieldInfo` objeto mediante una llamada a la `GetFieldInfo` función de miembro del objeto contenedor.  
  
 Además de su uso para examinar las propiedades de objeto, también puede utilizar `CDaoFieldInfo` para construir un parámetro de entrada para la creación de nuevos campos en una definición de tabla. Existen opciones más sencillos para esta tarea, pero si desea un control más preciso, puede utilizar la versión de [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) que toma un `CDaoFieldInfo` parámetro.  
  
 La información recuperada por la `GetFieldInfo` función miembro (de la clase que contiene el campo) se almacena en un `CDaoFieldInfo` estructura. Llame a la `GetFieldInfo` función de miembro del objeto contenedor en cuyo conjunto de campos se almacena el objeto de campo. `CDaoFieldInfo`También define un `Dump` se basa en la función miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de una `CDaoFieldInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)   
 [CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)   
 [CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)


