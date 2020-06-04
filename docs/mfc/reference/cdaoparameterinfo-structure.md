---
title: CDaoParameterInfo (Estructura)
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 6d594bbeec34e400eb074c136e3467e78b35c4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368977"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo (Estructura)

La `CDaoParameterInfo` estructura contiene información sobre un objeto de parámetro definido para objetos de acceso a datos (DAO). DAO 3.6 es la versión final, y se considera obsoleto.

## <a name="syntax"></a>Sintaxis

```
struct CDaoParameterInfo
{
    CString m_strName;       // Primary
    short m_nType;           // Primary
    ColeVariant m_varValue;  // Secondary
};
```

#### <a name="parameters"></a>Parámetros

*m_strName*<br/>
Asigna un nombre único al objeto de parámetro. Para obtener más información, vea el tema "Propiedad de nombre" en la Ayuda de DAO.

*m_nType*<br/>
Valor que indica el tipo de datos de un objeto de parámetro. Para obtener una lista de los valores posibles, vea el *m_nType* miembro de la [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Para obtener más información, vea el tema "Propiedad de tipo" en la Ayuda de DAO.

*m_varValue*<br/>
El valor del parámetro, almacenado en un [COleVariant](../../mfc/reference/colevariant-class.md) objeto.

## <a name="remarks"></a>Observaciones

Las referencias a las principales y secundarias anteriores indican cómo se devuelve la información mediante la función miembro [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) en la clase `CDaoQueryDef`.

MFC no encapsula los objetos de parámetro DAO en una clase. Los objetos de definición de consulta DAO subyacentes a los objetos MFC `CDaoQueryDef` almacenan parámetros en sus colecciones Parameters. Para tener acceso a los objetos de parámetro en un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objeto, llame a la función miembro del `GetParameterInfo` objeto querydef para un nombre de parámetro determinado o un índice en el Parameters colección. Puede usar el [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) función `GetParameterInfo` miembro junto con para recorrer en bucle el Parameters colección.

Información recuperada por el [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) función miembro se almacena en una `CDaoParameterInfo` estructura. Llame `GetParameterInfo` al objeto querydef en cuya colección Parameters se almacena el objeto de parámetro.

> [!NOTE]
> Si desea obtener o establecer solo el valor de un parámetro, utilice las funciones `CDaoRecordset`miembro [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) y [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) de la clase .

`CDaoParameterInfo`también define `Dump` una función miembro en compilaciones de depuración. Puede utilizar `Dump` para volcar `CDaoParameterInfo` el contenido de un objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="see-also"></a>Consulte también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Clase CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)
