---
title: Clase CMFCCmdUsageCount | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5b4824632d7ce38e50859172a24a47bdeb49f1d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369247"
---
# <a name="cmfccmdusagecount-class"></a>Clase CMFCCmdUsageCount
Realiza un seguimiento del contador de uso de mensajes de Windows, por ejemplo, cuando el usuario selecciona un elemento en un menú.  
  
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
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Se incrementa en uno el contador que está asociado con el comando determinado.|  
|[CMFCCmdUsageCount::GetCount](#getcount)|Recupera el recuento de uso que está asociado con el identificador de comando especificado.|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Determina si este objeto recopila la cantidad mínima de datos de seguimiento.|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Determina si el comando determinado se utiliza con frecuencia.|  
|[CMFCCmdUsageCount::Reset](#reset)|Borra el recuento de utilización de todos los comandos.|  
|[CMFCCmdUsageCount::Serialize](#serialize)|Lee este objeto desde un archivo o lo escribe en un archivo. (Invalida [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)).|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Establece los valores de comparten `CMFCCmdUsageCount` clase miembros de datos.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|nombre|Descripción|  
|`m_CmdUsage`|Un `CMap` objeto que asigna comandos a sus recuentos de uso.|  
|`m_nMinUsagePercentage`|El porcentaje de uso mínimo para un comando que se utilizará con frecuencia.|  
|`m_nStartCount`|El contador de inicio que se usa para determinar si este objeto recopila la cantidad mínima de datos de seguimiento.|  
|`m_nTotalUsage`|El número de comandos de todas las marcas.|  
  
### <a name="remarks"></a>Comentarios  
 La `CMFCCmdUsageCount` clase asigna cada identificador de mensaje de Windows numérico a un contador de entero sin signo de 32 bits. `CMFCToolBar` utiliza esta clase para mostrar los elementos de la barra de herramientas de uso frecuente. Para obtener más información acerca de `CMFCToolBar`, consulte [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md).  
  
 Puede conservar `CMFCCmdUsageCount` clase datos entre ejecuciones del programa. Use la [CMFCCmdUsageCount::Serialize](#serialize) método para serializar los datos de miembro de clase y el [CMFCCmdUsageCount::SetOptions](#setoptions) método para establecer los datos de miembro compartido.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmdusagecount.h  
  
##  <a name="addcmd"></a>  CMFCCmdUsageCount::AddCmd  
 Se incrementa en uno el contador que está asociado con el comando determinado.  
  
```  
void AddCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `uiCmd`|Especifica el contador de comando que se va a incrementar.|  
  
### <a name="remarks"></a>Comentarios  
 Este método agrega una nueva entrada a la estructura del mapa de recuentos de comando, `m_CmdUsage`, si la entrada no existe.  
  
 Este método no hace nada en los casos siguientes:  
  
-   El marco de trabajo de la barra de herramientas está en modo de personalización (la [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) método devuelve un valor distinto de cero).  
  
-   El comando hace referencia a un separador de menú o submenú ( `uiCmd` es igual a 0 o -1).  
  
- `uiCmd` hace referencia a un comando estándar (global `IsStandardCommand` función devuelve un valor distinto de cero).  
  
##  <a name="getcount"></a>  CMFCCmdUsageCount::GetCount  
 Recupera el recuento de uso que está asociado con el identificador de comando especificado.  
  
```  
UINT GetCount(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `uiCmd`|Identificador del contador de comando que se va a recuperar.|  
  
### <a name="return-value"></a>Valor devuelto  
 El contador de uso que está asociado con el identificador de comando especificado.  
  
##  <a name="hasenoughinformation"></a>  CMFCCmdUsageCount::HasEnoughInformation  
 Determina si este objeto ha recibido la cantidad mínima de datos de seguimiento.  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si este objeto ha recibido la cantidad mínima de seguimiento de los datos; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve un valor distinto de cero si el recuento total, `m_nTotalUsage`, de todas las marcas comandos es igual o mayor que el recuento inicial, `m_nStartCount`. De forma predeterminada, el marco de trabajo establece el recuento inicial de 0. Puede invalidar este valor utilizando la [CMFCCmdUsageCount::SetOptions](#setoptions) método.  
  
 Este método se usa por [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) para determinar si se muestran todos los comandos de menú disponibles.  
  
##  <a name="isfreqeuntlyusedcmd"></a>  CMFCCmdUsageCount::IsFreqeuntlyUsedCmd  
 Determina si el comando determinado se utiliza con frecuencia.  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `uiCmd`|Especifica el comando para comprobar.|  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el comando se usa frecuentemente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve 0 si el uso del comando total, `m_nTotalUsage`, es 0. En caso contrario, este método devuelve es distinto de cero si el porcentaje de los cuales se utiliza el comando especificado es mayor que el porcentaje mínimo, `m_nMinUsagePercentage`. De forma predeterminada, el marco de trabajo establece el porcentaje mínimo y 5. Puede invalidar este valor utilizando la [CMFCCmdUsageCount::SetOptions](#setoptions) método. Si el porcentaje mínimo es 0, este método devuelve es distinto de cero si el recuento de comando especificado es mayor que 0.  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) usa este método para determinar si un comando rara vez se usa.  
  
##  <a name="reset"></a>  CMFCCmdUsageCount::Reset  
 Borra el recuento de utilización de todos los comandos.  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para borrar todas las entradas de la estructura del mapa de recuentos de comando, `m_CmdUsage`y para restablecer el uso del comando total, `m_nTotalUsage`, contador en 0.  
  
##  <a name="serialize"></a>  CMFCCmdUsageCount::Serialize  
 Lee este objeto desde un archivo y lo escribe en un archivo.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `ar`|Un `CArchive` objeto que se va a serializar desde o hasta.|  
  
### <a name="remarks"></a>Comentarios  
 Este método serializa la estructura del mapa de recuentos de comando, `m_CmdUsage`y el uso del comando total, `m_nTotalUsage`, contador de o en el archivo especificado.  
  
 Para obtener ejemplos de serialización, vea [serialización: serializar un objeto](../../mfc/serialization-serializing-an-object.md).  
  
##  <a name="setoptions"></a>  CMFCCmdUsageCount::SetOptions  
 Establece los valores de comparten `CMFCCmdUsageCount` clase miembros de datos.  
  
```  
static BOOL __stdcall SetOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `nStartCount`|El nuevo recuento inicial de comandos todas las marcas.|  
|[in] `nMinUsagePercentage`|El porcentaje de uso mínimo de nuevo.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si el método tiene éxito, `FALSE` si el `nMinUsagePercentage` parámetro es mayor que o igual a 100.  
  
### <a name="remarks"></a>Comentarios  
 Este método establece el recurso compartido `CMFCCmdUsageCount` miembros de datos de clase `m_nStartCount` y `m_nMinUsagePercentage` a `nStartCount` y `nMinUsagePercentage`, respectivamente. `m_nStartCount` se usa por la [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) método para determinar si este objeto recopila la cantidad mínima de datos de seguimiento. `m_nMinUsagePercentage` se usa por la [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) método para determinar si un comando determinado se utiliza con frecuencia.  
  
 En las compilaciones de depuración este método genera un error de aserción si el `nMinUsagePercentage` parámetro es mayor que o igual a 100.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)
