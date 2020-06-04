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
ms.openlocfilehash: d91221dd509122ebbd6490c2de7fab1ce51eb2f8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210735"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl (Clase)

Proporciona una implementación para la interfaz [ICommandText](/previous-versions/windows/desktop/ms714914(v=vs.85)) .

## <a name="syntax"></a>Sintaxis

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase de comando derivada de `ICommandTextImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** altdb. h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[GetCommandText](#getcommandtext)|Devuelve el comando de texto establecido por la última llamada a [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).|
|[SetCommandText](#setcommandtext)|Establece el texto del comando, reemplazando el texto del comando existente.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_strCommandText](#strcommandtext)|Almacena el texto del comando.|

## <a name="remarks"></a>Observaciones

Interfaz obligatoria en comandos.

## <a name="icommandtextimplgetcommandtext"></a><a name="getcommandtext"></a>ICommandTextImpl:: GetCommandText

Devuelve el comando de texto establecido por la última llamada a [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>Parámetros

Vea [ICommandText:: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) en la *Referencia del programador de OLE DB*. De forma predeterminada, se omite el parámetro *pguidDialect* .

## <a name="icommandtextimplsetcommandtext"></a><a name="setcommandtext"></a>ICommandTextImpl:: SetCommandText

Establece el texto del comando, reemplazando el texto del comando existente.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>Parámetros

Vea [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="icommandtextimplm_strcommandtext"></a><a name="strcommandtext"></a>ICommandTextImpl:: m_strCommandText

Almacena la cadena de texto de comando.

### <a name="syntax"></a>Sintaxis

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
