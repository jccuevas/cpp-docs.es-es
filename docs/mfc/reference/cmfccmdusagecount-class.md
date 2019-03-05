---
title: CMFCCmdUsageCount (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::AddCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::GetCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::HasEnoughInformation
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Reset
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Serialize
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::SetOptions
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
ms.openlocfilehash: b4ad9a60831feb6fa1147ea3f8bcfd5c6badd06c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275368"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount (clase)

Realiza un seguimiento del recuento de uso de los mensajes de Windows, como cuando el usuario selecciona un elemento en un menú.

## <a name="syntax"></a>Sintaxis

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Name|Descripción|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Constructor predeterminado.|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Name|Descripción|
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Se incrementa en uno el contador que está asociado al comando especificado.|
|[CMFCCmdUsageCount::GetCount](#getcount)|Recupera el recuento de uso que está asociado con el identificador de comando especificado.|
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Determina si este objeto recopila la cantidad mínima de datos de seguimiento.|
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Determina si el comando determinado se utiliza con frecuencia.|
|[CMFCCmdUsageCount::Reset](#reset)|Borra el recuento de utilización de todos los comandos.|
|[CMFCCmdUsageCount::Serialize](#serialize)|Lee este objeto de un archivo o lo escribe en un archivo. (Invalida [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)).|
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Establece los valores de comparten `CMFCCmdUsageCount` miembros de datos de la clase.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|nombre|Descripción|
|`m_CmdUsage`|Un `CMap` objeto que asigna comandos a sus recuentos de uso.|
|`m_nMinUsagePercentage`|El porcentaje de uso mínimo de un comando que se usará con frecuencia.|
|`m_nStartCount`|El contador de inicio que se usa para determinar si este objeto recopila la cantidad mínima de datos de seguimiento.|
|`m_nTotalUsage`|El recuento de comandos de seguimiento del proceso.|

### <a name="remarks"></a>Comentarios

La `CMFCCmdUsageCount` clase asigna cada identificador numérico de mensaje de Windows a un contador de entero de 32 bits sin signo. `CMFCToolBar` Esta clase se utiliza para mostrar los elementos de la barra de herramientas usados con frecuencia. Para obtener más información acerca de `CMFCToolBar`, consulte [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md).

Puede conservar `CMFCCmdUsageCount` clase datos entre ejecuciones del programa. Use la [CMFCCmdUsageCount::Serialize](#serialize) método para serializar los datos de miembro de clase y el [CMFCCmdUsageCount::SetOptions](#setoptions) método para establecer los datos de miembro compartido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmdusagecount.h

##  <a name="addcmd"></a>  CMFCCmdUsageCount::AddCmd

Se incrementa en uno el contador que está asociado al comando especificado.

```
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*uiCmd*|[in] Especifica el contador de comando que se va a incrementar.|

### <a name="remarks"></a>Comentarios

Este método agrega una nueva entrada a la estructura del mapa de recuentos de comando, `m_CmdUsage`, si la entrada no existe ya.

Este método no hace nada en los casos siguientes:

- El marco de trabajo de la barra de herramientas está en modo de personalización (el [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) método devuelve un valor distinto de cero).

- El comando hace referencia a un separador de menú o submenú ( *uiCmd* es igual a 0 o -1).

- *uiCmd* hace referencia a un comando estándar (global `IsStandardCommand` función devuelve un valor distinto de cero).

##  <a name="getcount"></a>  CMFCCmdUsageCount::GetCount

Recupera el recuento de uso que está asociado con el identificador de comando especificado.

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*uiCmd*|[in] Identificador del contador de comando que se va a recuperar.|

### <a name="return-value"></a>Valor devuelto

El contador de uso que está asociado con el identificador de comando especificado.

##  <a name="hasenoughinformation"></a>  CMFCCmdUsageCount::HasEnoughInformation

Determina si este objeto ha recibido la cantidad mínima de datos de seguimiento.

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si este objeto ha recibido la cantidad mínima de seguimiento de los datos; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método devuelve un valor distinto de cero si el recuento total, `m_nTotalUsage`, de comandos de seguimiento del proceso es igual o mayor que el recuento inicial, `m_nStartCount`. De forma predeterminada, el marco de trabajo establece el recuento inicial de 0. Puede invalidar este valor utilizando la [CMFCCmdUsageCount::SetOptions](#setoptions) método.

Este método lo usa [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) para determinar si se muestran todos los comandos de menú disponibles.

##  <a name="isfreqeuntlyusedcmd"></a>  CMFCCmdUsageCount::IsFreqeuntlyUsedCmd

Determina si el comando determinado se utiliza con frecuencia.

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*uiCmd*|[in] Especifica el comando para comprobar.|

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el comando se usa con frecuencia; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método devuelve 0 si el uso del comando total, `m_nTotalUsage`, es 0. En caso contrario, este método devuelve cero si el porcentaje de los cuales se usa el comando especificado es mayor que el porcentaje mínimo, `m_nMinUsagePercentage`. De forma predeterminada, el marco de trabajo establece el porcentaje mínimo y 5. Puede invalidar este valor utilizando la [CMFCCmdUsageCount::SetOptions](#setoptions) método. Si el porcentaje mínimo es 0, este método devuelve cero si el recuento de comandos especificada es mayor que 0.

[CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) usa este método para determinar si un comando se usa con poca frecuencia.

##  <a name="reset"></a>  CMFCCmdUsageCount::Reset

Borra el recuento de utilización de todos los comandos.

```
void Reset();
```

### <a name="remarks"></a>Comentarios

Llame a este método para borrar todas las entradas de la estructura del mapa de recuentos de comando, `m_CmdUsage`y para restablecer el uso del comando total, `m_nTotalUsage`, contador en 0.

##  <a name="serialize"></a>  CMFCCmdUsageCount::Serialize

Lee este objeto de un archivo o lo escribe en un archivo.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*ar*|[in] Un `CArchive` objeto que se va a serializar desde o hacia.|

### <a name="remarks"></a>Comentarios

Este método serializa la estructura del mapa de recuentos de comando, `m_CmdUsage`y el uso del comando total, `m_nTotalUsage`, contador desde o al archivo especificado.

Para obtener ejemplos de serialización, vea [serialización: Serializar un objeto](../../mfc/serialization-serializing-an-object.md).

##  <a name="setoptions"></a>  CMFCCmdUsageCount::SetOptions

Establece los valores de comparten `CMFCCmdUsageCount` miembros de datos de la clase.

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*nStartCount*|[in] El nuevo recuento inicial de los comandos de seguimiento del proceso.|
|*nMinUsagePercentage*|[in] El porcentaje de uso mínimo de la nueva.|

### <a name="return-value"></a>Valor devuelto

TRUE si el método tiene éxito, FALSE si el *nMinUsagePercentage* parámetro es mayor o igual a 100.

### <a name="remarks"></a>Comentarios

Este método establece el recurso compartido `CMFCCmdUsageCount` miembros de datos de la clase `m_nStartCount` y `m_nMinUsagePercentage` a *nStartCount* y *nMinUsagePercentage*, respectivamente. `m_nStartCount` está usando el [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) método para determinar si este objeto recopila la cantidad mínima de datos de seguimiento. `m_nMinUsagePercentage` está usando el [Cmfccmdusagecount](#isfreqeuntlyusedcmd) método para determinar si un comando determinado se utiliza con frecuencia.

En las compilaciones de depuración este método genera un error de aserción si el *nMinUsagePercentage* parámetro es mayor o igual a 100.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)
