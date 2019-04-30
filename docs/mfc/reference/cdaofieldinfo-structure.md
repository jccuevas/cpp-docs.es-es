---
title: CDaoFieldInfo (Estructura)
ms.date: 11/04/2016
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: a5c4013a323c85ad19a3fade20f76852e053362a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399829"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo (Estructura)

El `CDaoFieldInfo` estructura contiene información sobre un objeto de campo definido para los objetos de acceso a datos (DAO).

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
Nombres de forma exclusiva el objeto de campo. Para obtener más información, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.

*m_nType*<br/>
Un valor que indica el tipo de datos del campo. Para obtener más información, vea el tema "Propiedad de tipo" en la Ayuda de DAO. El valor de esta propiedad puede ser uno de los siguientes:

- `dbBoolean` Sí/No, igual a TRUE o FALSE

- `dbByte` Byte

- `dbInteger` corto

- `dbLong` Long

- `dbCurrency` Moneda; clase MFC Vea [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle` único

- `dbDouble` Doble

- `dbDate` Fecha y hora; clase MFC Vea [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText` Texto; clase MFC Vea [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary` Binario largo (objeto OLE); desea usar la clase MFC [CByteArray](../../mfc/reference/cbytearray-class.md) en lugar de la clase `CLongBinary` como `CByteArray` es más rico y más fácil de usar.

- `dbMemo` Memorando; Consulte la clase MFC `CString`

- `dbGUID` Un identificador único global identificador/universalmente único usa con llamadas a procedimiento remoto. Para obtener más información, vea el tema "Propiedad de tipo" en la Ayuda de DAO.

> [!NOTE]
>  No utilice tipos de datos string para datos binarios. Esto hace que los datos pasar a través de la capa de conversión Unicode/ANSI, lo que produce una sobrecarga mayor y posiblemente inesperada de traducción.

*m_lSize*<br/>
Un valor que indica el tamaño máximo, en bytes, de un objeto de campo DAO que contiene texto o el tamaño de un objeto de campo que contiene valores numéricos o de texto fijo. Para obtener más información, vea el tema "Propiedad de tamaño" en la Ayuda de DAO. Tamaños de pueden ser uno de los siguientes valores:

|Tipo|Tamaño (bytes)|Descripción|
|----------|--------------------|-----------------|
|`dbBoolean`|1 byte|Sí/No (igual a True/False)|
|`dbByte`|1|Byte|
|`dbInteger`|2|Integer|
|`dbLong`|4|Long|
|`dbCurrency`|8|Moneda ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Doble|
|`dbDate`|8|Fecha y hora ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Texto ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Binario largo (objeto OLE; [CByteArray](../../mfc/reference/cbytearray-class.md); use en lugar de `CLongBinary`)|
|`dbMemo`|0|Memo ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Un identificador único global identificador/universalmente único usa con llamadas a procedimiento remoto.|

*m_lAttributes*<br/>
Especifica las características de un objeto de campo que contiene una definición de tabla, conjunto de registros, definición de consulta o el objeto de índice. El valor devuelto puede ser una suma de estas constantes, creado con C++ OR bit a bit (**&#124;**) operador:

- `dbFixedField` El tamaño del campo es fijo (valor predeterminado para los campos numéricos).

- `dbVariableField` El tamaño del campo es variable (sólo campos de texto).

- `dbAutoIncrField` El valor del campo para los nuevos registros se incrementa automáticamente a un único entero largo que no se puede cambiar. Solo se admite para las tablas de base de datos Microsoft Jet.

- `dbUpdatableField` Se puede cambiar el valor del campo.

- `dbDescending` El campo se ordena en orden descendente (Z - A 0 -100) orden (solo se aplica a un objeto de campo en una colección de campos de un objeto de índice; en MFC, ellos mismos objetos están contenidos en los objetos de definición de tabla de índice). Si se omite esta constante, el campo se ordena en orden ascendente (A - Z o 0 - 100) orden (valor predeterminado).

Cuando se comprueba el valor de esta propiedad, puede usar C++ bit a bit- y operador (**&**) para probar un atributo determinado. Al establecer varios atributos, puede combinarlas mediante la combinación de las constantes adecuadas con la operación bit a bit OR (**&#124;**) operador. Para obtener más información, vea el tema "Atributos de propiedad" en la Ayuda de DAO.

*m_nOrdinalPosition*<br/>
Un valor que especifica el orden numérico en el que desea que un campo representado por un objeto de campo DAO para mostrarse en relación con otros campos. Puede establecer esta propiedad con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Para obtener más información, vea el tema "Propiedad OrdinalPosition" en la Ayuda de DAO.

*m_bRequired*<br/>
Indica si un objeto de campo DAO requiere un valor distinto de Null. Si esta propiedad es TRUE, el campo no permite un valor Null. Si es necesario que se establece en FALSE, el campo puede contener valores Null, así como los valores que cumplen las condiciones especificadas por los valores de propiedad Permitir longitud cero y ValidationRule. Para obtener más información, vea el tema "Propiedad necesaria" en la Ayuda de DAO. Puede establecer esta propiedad para una definición de tabla con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_bAllowZeroLength*<br/>
Indica si una cadena vacía ("") es un valor válido de un objeto de campo DAO con un tipo de datos de texto o memorando. Si esta propiedad es TRUE, una cadena vacía es un valor válido. Puede establecer esta propiedad en FALSE para asegurarse de que no se puede usar una cadena vacía para establecer el valor de un campo. Para obtener más información, vea el tema "Propiedad Permitir longitud cero" en la Ayuda de DAO. Puede establecer esta propiedad para una definición de tabla con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_lCollatingOrder*<br/>
Especifica la secuencia del criterio de ordenación en el texto de comparación de cadenas u ordenación. Para obtener más información, vea el tema "Personalización de Windows del registro configuración de acceso a datos" en la Ayuda de DAO. Para obtener una lista de los posibles valores devueltos, vea el `m_lCollatingOrder` miembro de la [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) estructura. Puede establecer esta propiedad para una definición de tabla con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strForeignName*<br/>
Un valor que, en una relación, especifica el nombre del objeto de campo DAO en una tabla externa que corresponde a un campo en una tabla principal. Para obtener más información, vea el tema "Propiedad ForeignName" en la Ayuda de DAO.

*m_strSourceField*<br/>
Indica el nombre del campo que es el origen de los datos para un objeto de campo DAO contenido en una definición de tabla, conjunto de registros u objeto de definición de consulta. Esta propiedad indica el nombre del campo original asociado a un objeto de campo. Por ejemplo, podría utilizar esta propiedad para determinar el origen inicial de los datos en un campo de consulta cuyo nombre no está relacionado con el nombre del campo en la tabla subyacente. Para obtener más información, vea el tema "SourceField, SourceTable propiedades" en la Ayuda de DAO. Puede establecer esta propiedad para una definición de tabla con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strSourceTable*<br/>
Indica el nombre de la tabla que es el origen de los datos para un objeto de campo DAO contenido en una definición de tabla, conjunto de registros u objeto de definición de consulta. Esta propiedad indica el nombre de tabla original asociado a un objeto de campo. Por ejemplo, podría utilizar esta propiedad para determinar el origen inicial de los datos en un campo de consulta cuyo nombre no está relacionado con el nombre del campo en la tabla subyacente. Para obtener más información, vea el tema "SourceField, SourceTable propiedades" en la Ayuda de DAO. Puede establecer esta propiedad para una definición de tabla con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strValidationRule*<br/>
Un valor que valida los datos de un campo cuando se cambia o se agregan a una tabla. Para obtener más información, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO. Puede establecer esta propiedad para una definición de tabla con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

Para obtener información relacionada sobre definiciones de tabla, vea el `m_strValidationRule` miembro de la [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) estructura.

*m_strValidationText*<br/>
Un valor que especifica el texto del mensaje que la aplicación muestra si el valor de un objeto de campo DAO no cumple la regla de validación especificada por el valor de propiedad de ValidationRule. Para obtener más información, vea el tema "Propiedad de texto de validación" en la Ayuda de DAO. Puede establecer esta propiedad para una definición de tabla con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strDefaultValue*<br/>
El valor predeterminado de un objeto de campo DAO. Cuando se crea un nuevo registro, la propiedad DefaultValue se introduce automáticamente como el valor del campo. Para obtener más información, vea el tema "Propiedad DefaultValue" en la Ayuda de DAO. Puede establecer esta propiedad para una definición de tabla con [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

## <a name="remarks"></a>Comentarios

Las referencias a principal, secundaria y todo lo anterior indican cómo devuelve la información de la `GetFieldInfo` función miembro en clases [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo), y [ CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).

Los objetos de campo no están representados por una clase MFC. En su lugar, los objetos DAO de MFC objetos de las siguientes clases subyacentes contienen colecciones de objetos de campo: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), y [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Estas clases proporcionan funciones de miembro para tener acceso a algunos elementos individuales de información de campo, o puede tener acceso a ellos a la vez con un `CDaoFieldInfo` objeto mediante una llamada a la `GetFieldInfo` función de miembro del objeto contenedor.

Además de su uso para examinar las propiedades del objeto, también puede usar `CDaoFieldInfo` para construir un parámetro de entrada para la creación de nuevos campos en una definición de tabla. Existen opciones más sencillas para esta tarea, pero si desea un control más preciso, puede usar la versión de [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) que toma un `CDaoFieldInfo` parámetro.

Información recuperada por el `GetFieldInfo` función miembro (de la clase que contiene el campo) se almacena en un `CDaoFieldInfo` estructura. Llame a la `GetFieldInfo` función de miembro del objeto contenedor en cuya colección de campos se almacena el objeto de campo. `CDaoFieldInfo` También define un `Dump` se basa en función de miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoFieldInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
