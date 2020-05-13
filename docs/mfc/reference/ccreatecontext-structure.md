---
title: Estructura CCreateContext
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: 29fc6210b9888b6a5ba5aaf15b66242c29c15dc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369374"
---
# <a name="ccreatecontext-structure"></a>Estructura CCreateContext

El marco `CCreateContext` de trabajo utiliza la estructura cuando crea las ventanas de marco y las vistas asociadas a un documento.

## <a name="syntax"></a>Sintaxis

```
struct CCreateContext
```

## <a name="remarks"></a>Observaciones

`CCreateContext`es una estructura y no tiene una clase base.

Al crear una ventana, los valores de esta estructura proporcionan la información utilizada para conectar los componentes de un documento a la vista de sus datos. Sólo tiene que `CCreateContext` utilizar si está reemplazando partes del proceso de creación.

Una `CCreateContext` estructura contiene punteros al documento, la ventana de marco, la vista y la plantilla de documento. También contiene un puntero `CRuntimeClass` a un que identifica el tipo de vista que se va a crear. La información de clase en tiempo de ejecución y el puntero de documento actual se utilizan para crear una nueva vista dinámicamente. En la tabla siguiente se `CCreateContext` sugiere cómo y cuándo se puede utilizar cada miembro:

|Member|Tipo|Para qué sirve|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`de la nueva vista que se debe crear.|
|`m_pCurrentDoc`|`CDocument*`|El documento existente que se va a asociar a la nueva vista.|
|`m_pNewDocTemplate`|`CDocTemplate*`|La plantilla de documento asociada a la creación de una nueva ventana de marco MDI.|
|`m_pLastView`|`CView*`|La vista original en la que se modelan vistas adicionales, como en la creación de vistas de ventana divisora o la creación de una segunda vista en un documento.|
|`m_pCurrentFrame`|`CFrameWnd*`|La ventana de marco en la que se modelan ventanas de marco adicionales, como en la creación de una segunda ventana de marco en un documento.|

Cuando una plantilla de documento crea un documento y sus `CCreateContext` componentes asociados, valida la información almacenada en la estructura. Por ejemplo, no se debe crear una vista para un documento inexistente.

> [!NOTE]
> Todos los punteros `CCreateContext` en son `NULL` opcionales y pueden ser si no especificados o desconocidos.

`CCreateContext`es utilizado por las funciones miembro enumeradas en "Ver también." Consulte las descripciones de estas funciones para obtener información específica si tiene previsto anularlas.

Estas son algunas pautas generales:

- Cuando se pasa como argumento para `CWnd::Create` `CFrameWnd::Create`la `CFrameWnd::LoadFrame`creación de ventanas, como en , , y , el contexto de creación especifica a qué se debe conectar la nueva ventana. Para la mayoría de las ventanas, toda la estructura es opcional y se puede pasar un `NULL` puntero.

- Para funciones miembro reemplazables, `CFrameWnd::OnCreateClient` `CCreateContext` como , el argumento es opcional.

- Para las funciones miembro implicadas en la creación de vistas, debe proporcionar suficiente información para crear la vista. Por ejemplo, para la primera vista de una ventana divisora, debe proporcionar la información de clase de vista y el documento actual.

En general, si usa los valores predeterminados del marco de trabajo, puede omitir `CCreateContext`. Si intenta realizar modificaciones más avanzadas, el código fuente de la biblioteca Microsoft Foundation Class o los programas de ejemplo, como VIEWEX, le guiarán. Si olvida un parámetro necesario, una aserción de marco de trabajo le indicará lo que olvidó.

Para obtener `CCreateContext`más información sobre , vea el ejemplo [MFC VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Crear](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)
