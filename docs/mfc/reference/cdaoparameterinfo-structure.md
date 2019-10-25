---
title: CDaoParameterInfo (Estructura)
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 4f0ee7ebe1d5d4eff50194c2d5c5cccf8f373c61
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096075"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo (Estructura)

La `CDaoParameterInfo` estructura contiene información sobre un objeto de parámetro definido para los objetos de acceso a datos (DAO).
DAO 3,6 es la versión final y se considera obsoleta.


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
Designa de forma única el objeto de parámetro. Para obtener más información, vea el tema "propiedad Name" en la ayuda de DAO.

*m_nType*<br/>
Valor que indica el tipo de datos de un objeto de parámetro. Para obtener una lista de los valores posibles, vea el miembro *m_nType* de la estructura [cdaofieldinfo (](../../mfc/reference/cdaofieldinfo-structure.md) . Para obtener más información, vea el tema "Type Property" en la ayuda de DAO.

*m_varValue*<br/>
Valor del parámetro, almacenado en un objeto [COleVariant](../../mfc/reference/colevariant-class.md) .

## <a name="remarks"></a>Comentarios

Las referencias a las principales y secundarias anteriores indican cómo se devuelve la información mediante la función miembro [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) en la clase `CDaoQueryDef`.

MFC no encapsula objetos de parámetros de DAO en una clase. DAO QueryDef objetos subyacentes `CDaoQueryDef` los objetos MFC almacenan parámetros en sus colecciones de parámetros. Para tener acceso a los objetos de parámetro de un objeto [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) , llame a `GetParameterInfo` la función miembro del objeto QueryDef para un nombre de parámetro determinado o un índice en la colección Parameters. Puede usar la función miembro [CDaoQueryDef:: GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) junto con `GetParameterInfo` para recorrer la colección de parámetros.

La información recuperada por la función miembro [CDaoQueryDef:: GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) se almacena `CDaoParameterInfo` en una estructura. Llame `GetParameterInfo` al objeto QueryDef en cuya colección de parámetros se almacena el objeto de parámetro.

> [!NOTE]
>  Si solo desea obtener o establecer el valor de un parámetro, use las funciones miembro [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) y [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) de la clase `CDaoRecordset`.

`CDaoParameterInfo`también define una `Dump` función miembro en las compilaciones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoParameterInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)
