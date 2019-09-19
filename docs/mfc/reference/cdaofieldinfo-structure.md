---
title: CDaoFieldInfo (Estructura)
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: e98f5ba69f6702dd768cfe6605f993064e1b896c
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096099"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo (Estructura)

La `CDaoFieldInfo` estructura contiene información sobre un objeto de campo definido para los objetos de acceso a datos (DAO).

DAO es compatible con Office 2013. DAO 3,6 es la versión final y se considera obsoleta.

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

*m_strName*<br/>
Designa de forma única el objeto de campo. Para obtener más información, vea el tema "propiedad Name" en la ayuda de DAO.

*m_nType*<br/>
Valor que indica el tipo de datos del campo. Para obtener más información, vea el tema "propiedad de tipo" en la ayuda de DAO. El valor de esta propiedad puede ser uno de los siguientes:

- `dbBoolean`Sí/no, igual que verdadero/falso

- `dbByte`Bytes

- `dbInteger`Pequeño

- `dbLong`Tal

- `dbCurrency`Monetaria vea clase MFC [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle`Sencilla

- `dbDouble`Hace

- `dbDate`Fecha y hora; vea clase de MFC [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText`Negrita vea clase de MFC [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary`Long Binary (objeto OLE); es posible que desee usar la clase [CByteArray](../../mfc/reference/cbytearray-class.md) de MFC en lugar `CLongBinary` de `CByteArray` la clase, ya que es más rica y más fácil de usar.

- `dbMemo`Memorando vea clase MFC`CString`

- `dbGUID`Identificador único global o identificador único universal que se usa con llamadas a procedimientos remotos. Para obtener más información, vea el tema "Type Property" en la ayuda de DAO.

> [!NOTE]
>  No utilice tipos de datos de cadena para datos binarios. Esto hace que los datos pasen a través de la capa de conversión Unicode/ANSI, lo que produce una mayor sobrecarga y posiblemente una traducción inesperada.

*m_lSize*<br/>
Valor que indica el tamaño máximo, en bytes, de un objeto de campo DAO que contiene texto o el tamaño fijo de un objeto de campo que contiene valores de texto o numéricos. Para obtener más información, vea el tema "propiedad size" en la ayuda de DAO. Los tamaños pueden ser uno de los siguientes valores:

|Type|Tamaño (bytes)|DESCRIPCIÓN|
|----------|--------------------|-----------------|
|`dbBoolean`|1 byte|Sí/no (igual que verdadero/falso)|
|`dbByte`|1|Byte|
|`dbInteger`|2|Entero|
|`dbLong`|4|long|
|`dbCurrency`|8|Moneda ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|Fecha y hora ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Texto ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (objeto OLE; [CByteArray](../../mfc/reference/cbytearray-class.md); usar en lugar de `CLongBinary`)|
|`dbMemo`|0|Memorando ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Identificador único global o identificador único universal que se usa con llamadas a procedimientos remotos.|

*m_lAttributes*<br/>
Especifica las características de un objeto de campo que contiene un objeto TableDef, Recordset, QueryDef o index. El valor devuelto puede ser una suma de estas constantes, creadas con el C++ operador bit a bit **&#124;** or ():

- `dbFixedField`El tamaño del campo es fijo (valor predeterminado para los campos numéricos).

- `dbVariableField`El tamaño del campo es variable (solo campos de texto).

- `dbAutoIncrField`El valor del campo para los nuevos registros se incrementa automáticamente a un entero largo único que no se puede cambiar. Solo se admite para las tablas de base de datos de Microsoft Jet.

- `dbUpdatableField`Se puede cambiar el valor del campo.

- `dbDescending`El campo se ordena en orden descendente (Z-A o 100-0) (se aplica solo a un objeto de campo de una colección de campos de un objeto de índice; en MFC, los objetos de índice se encuentran en objetos tabledef). Si omite esta constante, el campo se ordena en orden ascendente (A-Z o 0-100) (valor predeterminado).

Al comprobar la configuración de esta propiedad, puede usar el C++ operador and bit a bit ( **&** ) para probar un atributo concreto. Al establecer varios atributos, puede combinarlos combinando las constantes adecuadas con el operador bit a bit or ( **&#124;** ). Para obtener más información, vea el tema "propiedad Attributes" en la ayuda de DAO.

*m_nOrdinalPosition*<br/>
Valor que especifica el orden numérico en el que desea que un campo representado por un objeto de campo DAO se muestre en relación con otros campos. Puede establecer esta propiedad con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Para obtener más información, vea el tema sobre la propiedad OrdinalPosition en la ayuda de DAO.

*m_bRequired*<br/>
Indica si un objeto de campo DAO requiere un valor distinto de NULL. Si esta propiedad es TRUE, el campo no permite un valor null. Si required se establece en FALSE, el campo puede contener valores NULL, así como valores que cumplen las condiciones especificadas por los valores de la propiedad AllowZeroLength y ValidationRule. Para obtener más información, vea el tema "propiedad Required" en la ayuda de DAO. Puede establecer esta propiedad para una definición de grupo con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_bAllowZeroLength*<br/>
Indica si una cadena vacía ("") es un valor válido de un objeto de campo DAO con un tipo de datos de texto o de memorando. Si esta propiedad es TRUE, una cadena vacía es un valor válido. Puede establecer esta propiedad en FALSE para asegurarse de que no se puede usar una cadena vacía para establecer el valor de un campo. Para obtener más información, vea el tema sobre la propiedad AllowZeroLength en la ayuda de DAO. Puede establecer esta propiedad para una definición de grupo con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_lCollatingOrder*<br/>
Especifica la secuencia del criterio de ordenación en texto para la comparación o ordenación de cadenas. Para obtener más información, vea el tema "personalizar la configuración del registro de Windows para el acceso a datos" en la ayuda de DAO. Para obtener una lista de los posibles valores devueltos `m_lCollatingOrder` , vea el miembro de la estructura [cdaodatabaseinfo (](../../mfc/reference/cdaodatabaseinfo-structure.md) . Puede establecer esta propiedad para una definición de grupo con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strForeignName*<br/>
Valor que, en una relación, especifica el nombre del objeto de campo DAO en una tabla externa que corresponde a un campo de una tabla principal. Para obtener más información, vea el tema "propiedad ForeignName" en la ayuda de DAO.

*m_strSourceField*<br/>
Indica el nombre del campo que es el origen original de los datos para un objeto de campo de DAO contenido en un objeto TableDef, Recordset o QueryDef. Esta propiedad indica el nombre de campo original asociado a un objeto de campo. Por ejemplo, podría utilizar esta propiedad para determinar el origen original de los datos en un campo de consulta cuyo nombre no está relacionado con el nombre del campo en la tabla subyacente. Para obtener información detallada, vea el tema "SourceField, SourceTable Properties" en la ayuda de DAO. Puede establecer esta propiedad para una definición de grupo con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strSourceTable*<br/>
Indica el nombre de la tabla que es el origen de los datos de un objeto de campo DAO contenido en un objeto TableDef, Recordset o QueryDef. Esta propiedad indica el nombre de tabla original asociado a un objeto de campo. Por ejemplo, podría utilizar esta propiedad para determinar el origen original de los datos en un campo de consulta cuyo nombre no está relacionado con el nombre del campo en la tabla subyacente. Para obtener información detallada, vea el tema "SourceField, SourceTable Properties" en la ayuda de DAO. Puede establecer esta propiedad para una definición de grupo con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strValidationRule*<br/>
Valor que valida los datos de un campo a medida que se cambian o se agregan a una tabla. Para obtener más información, vea el tema "propiedad ValidationRule" en la ayuda de DAO. Puede establecer esta propiedad para una definición de grupo con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

Para obtener información relacionada sobre TableDefs, `m_strValidationRule` vea el miembro de la estructura [cdaotabledefinfo (](../../mfc/reference/cdaotabledefinfo-structure.md) .

*m_strValidationText*<br/>
Valor que especifica el texto del mensaje que la aplicación muestra si el valor de un objeto de campo DAO no satisface la regla de validación especificada por el valor de la propiedad ValidationRule. Para obtener más información, vea el tema "propiedad ValidationText" en la ayuda de DAO. Puede establecer esta propiedad para una definición de grupo con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strDefaultValue*<br/>
Valor predeterminado de un objeto de campo DAO. Cuando se crea un nuevo registro, el valor de la propiedad DefaultValue se especifica automáticamente como el valor del campo. Para obtener más información, vea el tema "propiedad DefaultValue" en la ayuda de DAO. Puede establecer esta propiedad para una definición de grupo con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

## <a name="remarks"></a>Comentarios

Las referencias a principal, secundaria y todas las anteriores `GetFieldInfo` indican cómo devuelve la información la función miembro en las clases [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).

Los objetos de campo no se representan mediante una clase MFC. En su lugar, los objetos DAO subyacentes a objetos MFC de las clases siguientes contienen colecciones de objetos Field: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)y [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Estas clases proporcionan funciones miembro para tener acceso a algunos elementos individuales de la información de campo, o bien se puede tener acceso `CDaoFieldInfo` a ellas todas a `GetFieldInfo` la vez con un objeto llamando a la función miembro del objeto contenedor.

Además de su uso para examinar las propiedades de objeto, también puede `CDaoFieldInfo` usar para construir un parámetro de entrada para crear nuevos campos en una definición de objetos. Hay disponibles opciones más sencillas para esta tarea, pero si desea un control más preciso, puede usar la versión de [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) que toma un `CDaoFieldInfo` parámetro.

La información recuperada `GetFieldInfo` por la función miembro (de la clase que contiene el campo) se almacena `CDaoFieldInfo` en una estructura. Llame a `GetFieldInfo` la función miembro del objeto contenedor en cuya colección de campos se almacena el objeto de campo. `CDaoFieldInfo`también define una `Dump` función miembro en las compilaciones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoFieldInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
