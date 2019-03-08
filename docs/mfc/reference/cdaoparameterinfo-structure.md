---
title: CDaoParameterInfo (Estructura)
ms.date: 11/04/2016
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 62addd44f8aa8fceafef6a27244994a2ec6b766b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273951"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo (Estructura)

El `CDaoParameterInfo` estructura contiene información sobre un objeto de parámetro definido para los objetos de acceso a datos (DAO).

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
Nombres de forma exclusiva el objeto de parámetro. Para obtener más información, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.

*m_nType*<br/>
Un valor que indica el tipo de datos de un objeto de parámetro. Para obtener una lista de los valores posibles, vea el *m_nType* miembro de la [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Para obtener más información, vea el tema "Propiedad de tipo" en la Ayuda de DAO.

*m_varValue*<br/>
El valor del parámetro, almacenado en un [COleVariant](../../mfc/reference/colevariant-class.md) objeto.

## <a name="remarks"></a>Comentarios

Las referencias a principal y secundaria anterior indican cómo devuelve la información de la [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) función miembro de clase `CDaoQueryDef`.

MFC no encapsula los objetos de parámetro DAO en una clase. Objetos de definición de consulta DAO MFC subyacente `CDaoQueryDef` objetos almacenan los parámetros en sus colecciones de parámetros. Para obtener acceso a los objetos de parámetro en un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) de objetos, llamar al objeto de definición de consulta `GetParameterInfo` función miembro de un nombre de parámetro concreto o un índice en la colección de parámetros. Puede usar el [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) función miembro junto con `GetParameterInfo` para recorrer en iteración la colección de parámetros.

Información recuperada por el [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) función miembro se almacena en un `CDaoParameterInfo` estructura. Llame a `GetParameterInfo` para el objeto de definición de consulta en cuya colección de parámetros se almacena el objeto de parámetro.

> [!NOTE]
>  Si desea obtener o establecer solo el valor de un parámetro, use el [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) y [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) funciones miembro de clase `CDaoRecordset`.

`CDaoParameterInfo` También define un `Dump` se basa en función de miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoParameterInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)
