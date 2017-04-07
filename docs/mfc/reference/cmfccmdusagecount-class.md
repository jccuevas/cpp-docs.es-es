---
title: Clase CMFCCmdUsageCount | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CMFCCmdUsageCount class
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b264448af4041139018b181e2255988555267b89
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccmdusagecount-class"></a>Clase CMFCCmdUsageCount
Supervisa el contador de uso de mensajes de Windows, como cuando el usuario selecciona un elemento de un menú.  
  
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
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Se incrementa en uno el contador que está asociado al comando especificado.|  
|[CMFCCmdUsageCount::GetCount](#getcount)|Recupera el recuento de uso que está asociado con el identificador de comando especificado.|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Determina si este objeto recopila la cantidad mínima de datos de seguimiento.|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Determina si el comando especificado se utiliza con frecuencia.|  
|[CMFCCmdUsageCount::Reset](#reset)|Borra el recuento de uso de todos los comandos.|  
|[CMFCCmdUsageCount::Serialize](#serialize)|Lee este objeto desde un archivo o lo escribe en un archivo. (Invalida [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Establece los valores de comparten `CMFCCmdUsageCount` miembros de datos de la clase.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|`m_CmdUsage`|Un `CMap` objeto que asigna comandos a sus recuentos de uso.|  
|`m_nMinUsagePercentage`|El porcentaje de uso mínimo para un comando que se usará con frecuencia.|  
|`m_nStartCount`|El contador de inicio que se usa para determinar si este objeto recopila la cantidad mínima de datos de seguimiento.|  
|`m_nTotalUsage`|El número de comandos de todas las marcas.|  
  
### <a name="remarks"></a>Comentarios  
 La `CMFCCmdUsageCount` clase asigna cada identificador numérico de mensaje de Windows a un contador de 32 bits sin signo. `CMFCToolBar`Esta clase se utiliza para mostrar los elementos de la barra de herramientas de uso frecuente. Para obtener más información acerca de `CMFCToolBar`, consulte [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md).  
  
 Puede conservar `CMFCCmdUsageCount` clase datos entre ejecuciones del programa. Utilice la [CMFCCmdUsageCount::Serialize](#serialize) método para serializar los datos de miembros de clase y el [CMFCCmdUsageCount::SetOptions](#setoptions) para establecer los datos de miembro compartido.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmdusagecount.h  
  
##  <a name="addcmd"></a>CMFCCmdUsageCount::AddCmd  
 Se incrementa en uno el contador que está asociado al comando especificado.  
  
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
  
-   El marco de la barra de herramientas está en modo de personalización (la [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) método devuelve un valor distinto de cero).  
  
-   El comando hace referencia a un separador de menú o de submenú ( `uiCmd` es igual a 0 ó -1).  
  
- `uiCmd`hace referencia a un comando estándar (global `IsStandardCommand` función devuelve un valor distinto de cero).  
  
##  <a name="getcount"></a>CMFCCmdUsageCount::GetCount  
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
  
##  <a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation  
 Determina si este objeto ha recibido la cantidad mínima de datos de seguimiento.  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si este objeto ha recibido la cantidad mínima de seguimiento de los datos; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve un valor distinto de cero si el recuento total, `m_nTotalUsage`, de todas las marcas comandos es igual o mayor que el recuento inicial, `m_nStartCount`. De forma predeterminada, el marco de trabajo establece el recuento inicial de 0. Puede invalidar este valor utilizando la [CMFCCmdUsageCount::SetOptions](#setoptions) método.  
  
 Este método se usa por [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) para determinar si se muestran todos los comandos de menú disponibles.  
  
##  <a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd  
 Determina si el comando especificado se utiliza con frecuencia.  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `uiCmd`|Especifica el comando para comprobar.|  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el comando se usa frecuentemente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve 0 si el uso del comando total, `m_nTotalUsage`, es 0. De lo contrario, este método devuelve cero si el porcentaje de la que se utiliza el comando especificado es mayor que el porcentaje mínimo, `m_nMinUsagePercentage`. De forma predeterminada, el marco de trabajo establece el porcentaje mínimo de 5. Puede invalidar este valor utilizando la [CMFCCmdUsageCount::SetOptions](#setoptions) método. Si el porcentaje mínimo es 0, este método devuelve cero si el recuento de comando especificado es mayor que 0.  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) usa este método para determinar si un comando se utiliza muy poco.  
  
##  <a name="reset"></a>CMFCCmdUsageCount::Reset  
 Borra el recuento de uso de todos los comandos.  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para borrar todas las entradas de la estructura del mapa de recuentos de comando, `m_CmdUsage`y restablecer el uso del comando total, `m_nTotalUsage`, contador en 0.  
  
##  <a name="serialize"></a>CMFCCmdUsageCount::Serialize  
 Lee este objeto desde un archivo o lo escribe en un archivo.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `ar`|Un `CArchive` objeto para serializar desde o a.|  
  
### <a name="remarks"></a>Comentarios  
 Este método serializa la estructura del mapa de recuentos de comando, `m_CmdUsage`y el uso del comando total, `m_nTotalUsage`, contador desde o hacia el archivo especificado.  
  
 Para obtener ejemplos de serialización, vea [serialización: serializar un objeto](../../mfc/serialization-serializing-an-object.md).  
  
##  <a name="setoptions"></a>CMFCCmdUsageCount::SetOptions  
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
|[in] `nStartCount`|El nuevo recuento inicial de comandos todas las marcas.|  
|[in] `nMinUsagePercentage`|El porcentaje de uso mínimo de nuevo.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito, `FALSE` si el `nMinUsagePercentage` parámetro es mayor o igual a 100.  
  
### <a name="remarks"></a>Comentarios  
 Este método establece el recurso compartido `CMFCCmdUsageCount` miembros de datos de la clase `m_nStartCount` y `m_nMinUsagePercentage` a `nStartCount` y `nMinUsagePercentage`, respectivamente. `m_nStartCount`utiliza la [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) método para determinar si este objeto recopila la cantidad mínima de datos de seguimiento. `m_nMinUsagePercentage`utiliza la [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) método para determinar si un comando determinado se utiliza con frecuencia.  
  
 En compilaciones de depuración este método genera un error de aserción si el `nMinUsagePercentage` parámetro es mayor o igual a 100.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

