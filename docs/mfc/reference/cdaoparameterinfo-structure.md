---
title: CDaoParameterInfo (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoParameterInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ef473912489e9c757574545be2f8a53d7f3f9b9
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951606"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo (Estructura)
El `CDaoParameterInfo` estructura contiene información sobre un objeto de parámetro definido para objetos de acceso a datos (DAO).  
  
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
 *m_strName*  
 Identifica inequívocamente el objeto de parámetro. Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
 *m_nType*  
 Un valor que indica el tipo de datos de un objeto de parámetro. Para obtener una lista de los valores posibles, vea el *m_nType* miembro de la [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Para obtener más información, vea el tema "Tipo de propiedad" en la Ayuda de DAO.  
  
 *m_varValue*  
 El valor del parámetro, almacenado en una [COleVariant](../../mfc/reference/colevariant-class.md) objeto.  
  
## <a name="remarks"></a>Comentarios  
 Las referencias a principal y secundaria anterior indican cómo se devuelve la información de la [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) función de miembro de clase `CDaoQueryDef`.  
  
 MFC no encapsula los objetos de parámetro DAO en una clase. Definición de consulta DAO objetos MFC subyacente `CDaoQueryDef` objetos almacenan parámetros en las colecciones de parámetros. Para obtener acceso a los objetos de parámetro en un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) de objeto, llame al objeto de definición de consulta `GetParameterInfo` función de miembro para un nombre de parámetro concreto o un índice en la colección de parámetros. Puede usar el [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) función miembro junto con `GetParameterInfo` para recorrer en iteración la colección de parámetros.  
  
 La información recuperada por la [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) función miembro se almacena en un `CDaoParameterInfo` estructura. Llame a `GetParameterInfo` para el objeto de definición de consulta en cuya colección de parámetros se almacena el objeto de parámetro.  
  
> [!NOTE]
>  Si desea obtener o establecer solo el valor de un parámetro, use la [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) y [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) funciones miembro de clase `CDaoRecordset`.  
  
 `CDaoParameterInfo` También define un `Dump` compila la función miembro en versiones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoParameterInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)
