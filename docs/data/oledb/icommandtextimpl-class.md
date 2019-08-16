---
title: ICommandTextImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ICommandText
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
- ATL::ICommandTextImpl::m_strCommandText
- ICommandTextImpl<T>::m_strCommandText
- m_strCommandText
- ICommandTextImpl.m_strCommandText
- ICommandTextImpl::m_strCommandText
- ATL::ICommandTextImpl<T>::m_strCommandText
- ATL.ICommandTextImpl.m_strCommandText
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
ms.openlocfilehash: de9e930056db7b91968ca1ce471a87809693376a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408984"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl (Clase)

Proporciona una implementación para el [ICommandText](/previous-versions/windows/desktop/ms714914(v=vs.85)) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Deriva de la clase de comando `ICommandTextImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** altdb.h

## <a name="members"></a>Miembros

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[GetCommandText](#getcommandtext)|Devuelve el comando de texto establecido por la última llamada a [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).|
|[SetCommandText](#setcommandtext)|Establece el texto del comando, reemplazando el texto del comando existente.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_strCommandText](#strcommandtext)|Almacena el texto del comando.|

## <a name="remarks"></a>Comentarios

Una interfaz obligatoria en los comandos.

## <a name="getcommandtext"></a> ICommandTextImpl::GetCommandText

Devuelve el comando de texto establecido por la última llamada a [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>Parámetros

Consulte [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) en el *referencia del programador OLE DB*. El *pguidDialect* se omite el parámetro de forma predeterminada.

## <a name="setcommandtext"></a> ICommandTextImpl::SetCommandText

Establece el texto del comando, reemplazando el texto del comando existente.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>Parámetros

Consulte [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) en el *referencia del programador OLE DB*.

## <a name="strcommandtext"></a> ICommandTextImpl::m_strCommandText

Almacena la cadena de texto de comando.

### <a name="syntax"></a>Sintaxis

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)