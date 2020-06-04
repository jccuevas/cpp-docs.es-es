---
title: CDaoFieldInfo (Estructura)
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: 9466386fefc6e5ab8fcf89bf497c1d5219e3e807
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368409"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo (Estructura)

La `CDaoFieldInfo` estructura contiene información sobre un objeto de campo definido para objetos de acceso a datos (DAO).

DAO se admite a través de Office 2013. DAO 3.6 es la versión final, y se considera obsoleto.

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
Asigna un nombre único al objeto de campo. Para obtener más información, consulte el tema "Propiedad de nombre" en la Ayuda de DAO.

*m_nType*<br/>
Valor que indica el tipo de datos del campo. Para obtener más información, consulte el tema "Propiedad de tipo" en la Ayuda de DAO. El valor de esta propiedad puede ser uno de los siguientes:

- `dbBoolean`Sí/No, igual que VERDADERO/FALSO

- `dbByte`Byte

- `dbInteger`Corto

- `dbLong`Largo

- `dbCurrency`Moneda; vea la clase MFC [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle`soltero

- `dbDouble`Doble

- `dbDate`Fecha/Hora; vea la clase MFC [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText`Texto; vea la clase MFC [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary`Long Binary (objeto OLE); es posible que desee utilizar la `CLongBinary` clase `CByteArray` MFC [CByteArray](../../mfc/reference/cbytearray-class.md) en lugar de la clase, ya que es más rico y fácil de usar.

- `dbMemo`Memo; ver clase MFC`CString`

- `dbGUID`Identificador único global/identificador único universal utilizado con llamadas a procedimientos remotos. Para obtener más información, vea el tema "Propiedad de tipo" en la Ayuda de DAO.

> [!NOTE]
> No utilice tipos de datos de cadena para datos binarios. Esto hace que los datos pasen a través de la capa de traducción Unicode/ANSI, lo que aumenta la sobrecarga y posiblemente la traducción inesperada.

*m_lSize*<br/>
Valor que indica el tamaño máximo, en bytes, de un objeto de campo DAO que contiene texto o el tamaño fijo de un objeto de campo que contiene texto o valores numéricos. Para obtener más información, consulte el tema "Propiedad de tamaño" en la Ayuda de DAO. Los tamaños pueden ser uno de los siguientes valores:

|Tipo|Tamaño (bytes)|Descripción|
|----------|--------------------|-----------------|
|`dbBoolean`|1 byte|Sí/No (igual que Verdadero/Falso)|
|`dbByte`|1|Byte|
|`dbInteger`|2|Entero|
|`dbLong`|4|long|
|`dbCurrency`|8|Moneda ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|Fecha/Hora ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Texto ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (objeto OLE; [CByteArray](../../mfc/reference/cbytearray-class.md); uso en `CLongBinary`lugar de )|
|`dbMemo`|0|Memo ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Identificador único global/identificador único universal utilizado con llamadas a procedimientos remotos.|

*m_lAttributes*<br/>
Especifica las características de un objeto de campo contenido en una definición de tabla, un conjunto de registros, una definición de consulta o un objeto de índice. El valor devuelto puede ser una suma de estas constantes, creadas con el operador C++ bit a bit OR (**&#124;**):

- `dbFixedField`El tamaño del campo es fijo (predeterminado para los campos numéricos).

- `dbVariableField`El tamaño del campo es variable (solo campos de texto).

- `dbAutoIncrField`El valor de campo para los nuevos registros se incrementa automáticamente en un entero largo único que no se puede cambiar. Solo se admite para tablas de base de datos de Microsoft Jet.

- `dbUpdatableField`El valor del campo se puede cambiar.

- `dbDescending`El campo se ordena en orden descendente (Z - A o 100 - 0) (solo se aplica a un objeto de campo de una colección Fields de un objeto de índice; en MFC, los objetos de índice están contenidos en objetos de base de tabla). Si omite esta constante, el campo se ordena en orden ascendente (A - Z o 0 - 100) (predeterminado).

Al comprobar la configuración de esta propiedad, puede usar el**&** operador AND bit a bit ( ) para probar un atributo específico. Al establecer varios atributos, puede combinarlos combinando las constantes adecuadas con el operador OR (**&#124;**) bit a bit. Para obtener más información, consulte el tema "Propiedad de atributos" en la Ayuda de DAO.

*m_nOrdinalPosition*<br/>
Valor que especifica el orden numérico en el que desea que se muestre un campo representado por un objeto de campo DAO en relación con otros campos. Puede establecer esta propiedad con [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Para obtener más información, consulte el tema "Propiedad OrdinalPosition" en la Ayuda de DAO.

*m_bRequired*<br/>
Indica si un objeto de campo DAO requiere un valor distinto de Null. Si esta propiedad es TRUE, el campo no permite un valor Null. Si Required se establece en FALSE, el campo puede contener valores Null, así como valores que cumplen las condiciones especificadas por la configuración de la propiedad AllowZeroLength y ValidationRule. Para obtener más información, consulte el tema "Propiedad requerida" en la Ayuda de DAO. Puede establecer esta propiedad para una unidad de tabla con [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_bAllowZeroLength*<br/>
Indica si una cadena vacía ("") es un valor válido de un objeto de campo DAO con un tipo de datos Text o Memo. Si esta propiedad es TRUE, una cadena vacía es un valor válido. Puede establecer esta propiedad en FALSE para asegurarse de que no puede usar una cadena vacía para establecer el valor de un campo. Para obtener más información, consulte el tema "Propiedad AllowZeroLength" en la Ayuda de DAO. Puede establecer esta propiedad para una unidad de tabla con [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_lCollatingOrder*<br/>
Especifica la secuencia del criterio de ordenación en el texto para la comparación u ordenación de cadenas. Para obtener más información, consulte el tema "Personalización de la configuración del Registro de Windows para el acceso a datos" en la Ayuda de DAO. Para obtener una lista de los `m_lCollatingOrder` valores posibles devueltos, vea el miembro de la [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) estructura. Puede establecer esta propiedad para una unidad de tabla con [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strForeignName*<br/>
Valor que, en una relación, especifica el nombre del objeto de campo DAO en una tabla externa que corresponde a un campo de una tabla principal. Para obtener más información, consulte el tema "ForeignName Property" en la Ayuda de DAO.

*m_strSourceField*<br/>
Indica el nombre del campo que es el origen original de los datos de un objeto de campo DAO contenido por una definición de tabla, un conjunto de registros o un objeto de definición de consulta. Esta propiedad indica el nombre de campo original asociado a un objeto de campo. Por ejemplo, podría usar esta propiedad para determinar el origen original de los datos en un campo de consulta cuyo nombre no está relacionado con el nombre del campo de la tabla subyacente. Para obtener más información, vea el tema "SourceField, Propiedades de SourceTable" en la Ayuda de DAO. Puede establecer esta propiedad para una unidad de tabla con [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strSourceTable*<br/>
Indica el nombre de la tabla que es el origen original de los datos de un objeto de campo DAO contenido por una definición de tabla, un conjunto de registros o un objeto de definición de consulta. Esta propiedad indica el nombre de tabla original asociado a un objeto de campo. Por ejemplo, podría usar esta propiedad para determinar el origen original de los datos en un campo de consulta cuyo nombre no está relacionado con el nombre del campo de la tabla subyacente. Para obtener más información, vea el tema "SourceField, Propiedades de SourceTable" en la Ayuda de DAO. Puede establecer esta propiedad para una unidad de tabla con [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strValidationRule*<br/>
Valor que valida los datos de un campo a medida que se cambian o se agregan a una tabla. Para obtener más información, consulte el tema "Propiedad ValidationRule" en la Ayuda de DAO. Puede establecer esta propiedad para una unidad de tabla con [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

Para obtener información relacionada acerca de `m_strValidationRule` tabledefs, vea el miembro de la [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) estructura.

*m_strValidationText*<br/>
Valor que especifica el texto del mensaje que muestra la aplicación si el valor de un objeto de campo DAO no satisface la regla de validación especificada por el valor de la propiedad ValidationRule. Para obtener más información, vea el tema "Propiedad ValidationText" en la Ayuda de DAO. Puede establecer esta propiedad para una unidad de tabla con [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strDefaultValue*<br/>
El valor predeterminado de un objeto de campo DAO. Cuando se crea un nuevo registro, el valor de la propiedad DefaultValue se especifica automáticamente como el valor del campo. Para obtener más información, vea el tema "Propiedad DefaultValue" en la Ayuda de DAO. Puede establecer esta propiedad para una unidad de tabla con [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

## <a name="remarks"></a>Observaciones

Las referencias a Primary, Secondary y All anteriores `GetFieldInfo` indican cómo devuelve la información la función miembro en las clases [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).

Los objetos de campo no se representan mediante una clase MFC. En su lugar, los objetos DAO subyacentes a objetos MFC de las clases siguientes contienen colecciones de objetos de campo: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)y [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Estas clases proporcionan funciones miembro para tener acceso a algunos elementos `CDaoFieldInfo` individuales `GetFieldInfo` de información de campo, o puede tener acceso a todos ellos a la vez con un objeto mediante una llamada a la función miembro del objeto contenedor.

Además de su uso para examinar `CDaoFieldInfo` las propiedades del objeto, también puede utilizar para construir un parámetro de entrada para crear nuevos campos en una referencia de tabla. Las opciones más sencillas están disponibles para esta tarea, pero si desea un control más preciso, `CDaoFieldInfo` puede usar la versión de [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) que toma un parámetro.

La información recuperada por la `GetFieldInfo` función miembro (de la `CDaoFieldInfo` clase que contiene el campo) se almacena en una estructura. Llame `GetFieldInfo` a la función miembro del objeto contenedor en cuya colección Fields se almacena el objeto de campo. `CDaoFieldInfo`también define `Dump` una función miembro en compilaciones de depuración. Puede utilizar `Dump` para volcar `CDaoFieldInfo` el contenido de un objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="see-also"></a>Consulte también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
