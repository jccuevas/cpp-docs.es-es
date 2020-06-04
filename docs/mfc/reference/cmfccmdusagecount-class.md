---
title: CMFCCmdUsageCount (Clase)
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
ms.openlocfilehash: 02b302ec38922128190a6f20ce2f156b52383b55
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752584"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount (Clase)

Realiza un seguimiento del recuento de uso de los mensajes de Windows, como cuando el usuario selecciona un elemento de un menú.

## <a name="syntax"></a>Sintaxis

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Constructor predeterminado.|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Incrementa en uno el contador asociado al comando dado.|
|[CMFCCmdUsageCount::GetCount](#getcount)|Recupera el recuento de uso asociado al identificador de comando especificado.|
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Determina si este objeto ha recopilado la cantidad mínima de datos de seguimiento.|
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Determina si el comando dado se utiliza con frecuencia.|
|[CMFCCmdUsageCount::Reset](#reset)|Borra el recuento de uso de todos los comandos.|
|[CMFCCmdUsageCount::Serialize](#serialize)|Lee este objeto de un archivo o lo escribe en un archivo. (Invalida [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)).|
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Establece los valores `CMFCCmdUsageCount` de los miembros de datos de clase compartidos.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|Nombre|Descripción|
|`m_CmdUsage`|Un `CMap` objeto que asigna comandos a sus recuentos de uso.|
|`m_nMinUsagePercentage`|Porcentaje de uso mínimo para un comando que se va a utilizar con frecuencia.|
|`m_nStartCount`|El contador de inicio que se utiliza para determinar si este objeto ha recopilado la cantidad mínima de datos de seguimiento.|
|`m_nTotalUsage`|El recuento de todos los comandos rastreados.|

### <a name="remarks"></a>Observaciones

La `CMFCCmdUsageCount` clase asigna cada identificador numérico de mensaje de Windows a un contador de enteros sin signo de 32 bits. `CMFCToolBar`utiliza esta clase para mostrar los elementos de barra de herramientas utilizados con frecuencia. Para obtener `CMFCToolBar`más información acerca de , vea [CMFCToolBar (Clase).](../../mfc/reference/cmfctoolbar-class.md)

Puede conservar `CMFCCmdUsageCount` los datos de clase entre ejecuciones del programa. Utilice el [método CMFCCmdUsageCount::Serialize](#serialize) para serializar los datos de miembro de clase y el método [CMFCCmdUsageCount::SetOptions](#setoptions) para establecer datos de miembro compartidos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmdusagecount.h

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a>CMFCCmdUsageCount::AddCmd

Incrementa en uno el contador asociado al comando dado.

```cpp
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*uiCmd*|[en] Especifica el contador de comandos que se va a incrementar.|

### <a name="remarks"></a>Observaciones

Este método agrega una nueva entrada a la `m_CmdUsage`estructura de mapa de recuentos de comandos, , si la entrada aún no existe.

Este método no hace nada en los siguientes casos:

- El marco de trabajo de la barra de herramientas está en modo de personalización (el [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) método devuelve un valor distinto de cero).

- El comando hace referencia a un submenú o separador de menú ( *uiCmd* es igual a 0 o -1).

- *uiCmd* hace referencia a un `IsStandardCommand` comando estándar (la función global devuelve un valor distinto de cero).

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a>CMFCCmdUsageCount::GetCount

Recupera el recuento de uso asociado al identificador de comando especificado.

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*uiCmd*|[en] El IDENTIFICADOR del contador de comandos que se va a recuperar.|

### <a name="return-value"></a>Valor devuelto

El recuento de uso asociado al identificador de comando especificado.

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation

Determina si este objeto ha recibido la cantidad mínima de datos de seguimiento.

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si este objeto ha recibido la cantidad mínima de datos de seguimiento; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método devuelve un valor distinto `m_nTotalUsage`de cero si el recuento total, , de `m_nStartCount`todos los comandos rastreados es igual o mayor que el recuento inicial, . De forma predeterminada, el marco de trabajo establece el recuento inicial 0. Puede invalidar este valor mediante el [CMFCCmdUsageCount::SetOptions](#setoptions) método.

[CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) utiliza este método para determinar si se deben mostrar todos los comandos de menú disponibles.

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd

Determina si el comando dado se utiliza con frecuencia.

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*uiCmd*|[en] Especifica el comando que se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el comando se utiliza con frecuencia; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método devuelve 0 si `m_nTotalUsage`el uso total del comando, , es 0. De lo contrario, este método devuelve distinto de cero si el porcentaje `m_nMinUsagePercentage`del que se utiliza el comando especificado es mayor que el porcentaje mínimo, . De forma predeterminada, el marco de trabajo establece el porcentaje mínimo en 5. Puede invalidar este valor mediante el [CMFCCmdUsageCount::SetOptions](#setoptions) método. Si el porcentaje mínimo es 0, este método devuelve distinto de cero si el recuento de comandos especificado es mayor que 0.

[CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) utiliza este método para determinar si un comando rara vez se utiliza.

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a>CMFCCmdUsageCount::Reset

Borra el recuento de uso de todos los comandos.

```cpp
void Reset();
```

### <a name="remarks"></a>Observaciones

Llame a este método para borrar todas las `m_CmdUsage`entradas de la estructura de `m_nTotalUsage`mapa de los recuentos de comandos, y para restablecer el uso total del comando, , counter a 0.

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a>CMFCCmdUsageCount::Serialize

Lee este objeto de un archivo o lo escribe en un archivo.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*Ar*|[en] Objeto `CArchive` desde o desde el que serializar.|

### <a name="remarks"></a>Observaciones

Este método serializa la estructura de `m_CmdUsage`mapa de los `m_nTotalUsage`recuentos de comandos, y el uso total de comandos, , contador desde o hacia el archivo especificado.

Para obtener ejemplos de serialización, vea [Serialización: serialización](../../mfc/serialization-serializing-an-object.md)de un objeto .

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a>CMFCCmdUsageCount::SetOptions

Establece los valores `CMFCCmdUsageCount` de los miembros de datos de clase compartidos.

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*nStartCount*|[en] El nuevo recuento inicial de todos los comandos rastreados.|
|*nMinUsagePercentage*|[en] El nuevo porcentaje mínimo de uso.|

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realiza correctamente, FALSE si el *nMinUsagePercentage* parámetro es mayor o igual que 100.

### <a name="remarks"></a>Observaciones

Este método establece `CMFCCmdUsageCount` los `m_nStartCount` miembros de datos de clase compartida y `m_nMinUsagePercentage` *nStartCount* y *nMinUsagePercentage*, respectivamente. `m_nStartCount`lo utiliza el método [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) para determinar si este objeto ha recopilado la cantidad mínima de datos de seguimiento. `m_nMinUsagePercentage`lo utiliza el método [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) para determinar si un comando determinado se utiliza con frecuencia.

En Debug compila este método genera un error de aserción si el *nMinUsagePercentage* parámetro es mayor o igual que 100.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (Clase)](../../mfc/reference/cmfctoolbar-class.md)
