---
title: CDaoParameterInfo (Estructura)
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 9f96cba8ea43db7e24e834b1de4ffb593b2c6e0d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303492"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo (Estructura)

La estructura `CDaoParameterInfo` contiene información sobre un objeto de parámetro definido para los objetos de acceso a datos (DAO). DAO 3,6 es la versión final y se considera obsoleta.

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
Valor que indica el tipo de datos de un objeto de parámetro. Para obtener una lista de los valores posibles, vea el *m_nType* miembro de la estructura [cdaofieldinfo (](../../mfc/reference/cdaofieldinfo-structure.md) . Para obtener más información, vea el tema "Type Property" en la ayuda de DAO.

*m_varValue*<br/>
Valor del parámetro, almacenado en un objeto [COleVariant](../../mfc/reference/colevariant-class.md) .

## <a name="remarks"></a>Comentarios

Las referencias a las principales y secundarias anteriores indican cómo se devuelve la información mediante la función miembro [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) en la clase `CDaoQueryDef`.

MFC no encapsula objetos de parámetros de DAO en una clase. Objetos QueryDef de DAO subyacentes objetos de `CDaoQueryDef` MFC almacenan parámetros en sus colecciones de parámetros. Para tener acceso a los objetos de parámetro de un objeto [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) , llame a la función miembro `GetParameterInfo` del objeto QueryDef para un nombre de parámetro determinado o un índice en la colección Parameters. Puede usar la función miembro [CDaoQueryDef:: GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) junto con `GetParameterInfo` para recorrer en bucle la colección de parámetros.

La información recuperada por la función miembro [CDaoQueryDef:: GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) se almacena en una estructura de `CDaoParameterInfo`. Llame a `GetParameterInfo` para el objeto QueryDef en cuya colección de parámetros se almacena el objeto de parámetro.

> [!NOTE]
>  Si solo desea obtener o establecer el valor de un parámetro, use las funciones miembro [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) y [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) de la clase `CDaoRecordset`.

`CDaoParameterInfo` también define una función miembro de `Dump` en las compilaciones de depuración. Puede usar `Dump` para volcar el contenido de un objeto `CDaoParameterInfo`.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)
