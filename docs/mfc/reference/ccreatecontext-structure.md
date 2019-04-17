---
title: CCreateContext (estructura)
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: 795b20cba41eeca8cc1a32e312edf065b718f364
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768491"
---
# <a name="ccreatecontext-structure"></a>CCreateContext (estructura)

El marco de trabajo usa el `CCreateContext` estructura cuando crea las ventanas de marco y vistas que están asociadas con un documento.

## <a name="syntax"></a>Sintaxis

```
struct CCreateContext
```

## <a name="remarks"></a>Comentarios

`CCreateContext` es una estructura y no tiene una clase base.

Cuando se crea una ventana, los valores de esta estructura proporcionan la información que se usa para conectar los componentes de un documento a la vista de sus datos. Solo tiene que usar `CCreateContext` si va a reemplazar partes del proceso de creación.

Un `CCreateContext` estructura contiene punteros a la plantilla de documento, la ventana de marco, la vista y el documento. También contiene un puntero a un `CRuntimeClass` que identifica el tipo de vista para crear. La información de clase en tiempo de ejecución y el puntero del documento actual se utilizan para crear una nueva vista de forma dinámica. La siguiente tabla se sugiere cómo y cuándo cada `CCreateContext` podría utilizarse el miembro:

|Miembro|Tipo|¿Qué es|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` de la nueva vista para crear.|
|`m_pCurrentDoc`|`CDocument*`|El documento existente que se asociará con la nueva vista.|
|`m_pNewDocTemplate`|`CDocTemplate*`|La plantilla de documento asociada con la creación de una nueva ventana de marco MDI.|
|`m_pLastView`|`CView*`|La vista original en el que se modelan vistas adicionales, como se muestra en la creación de vistas de la ventana divisora o la creación de una segunda vista en un documento.|
|`m_pCurrentFrame`|`CFrameWnd*`|La ventana de marco en el que se modelan ventanas de marco adicional, como se muestra en la creación de una segunda ventana de marco en un documento.|

Cuando una plantilla de documento crea un documento y sus componentes asociados, valida la información almacenada en el `CCreateContext` estructura. Por ejemplo, no debe crearse una vista para un documento que no existe.

> [!NOTE]
>  Todos los punteros de `CCreateContext` son opcionales y pueden ser `NULL` si ha especificado o desconocido.

`CCreateContext` se utiliza por las funciones miembro que aparece en "Vea también". Si va a invalidarlos, consulte las descripciones de estas funciones para obtener información específica.

Estas son algunas directrices generales:

- Cuando se pasa como un argumento para la creación de la ventana, como en `CWnd::Create`, `CFrameWnd::Create`, y `CFrameWnd::LoadFrame`, el contexto de creación especifica lo que la nueva ventana debe estar conectada a. Para la mayoría de las ventanas, la estructura completa es opcional y un `NULL` se puede pasar el puntero.

- Para las funciones miembro reemplazables, tales como `CFrameWnd::OnCreateClient`, el `CCreateContext` argumento es opcional.

- Para las funciones miembro implicadas en la vista creación, debe proporcionar suficiente información para crear la vista. Por ejemplo, para la primera vista en una ventana divisora, debe proporcionar la información de la clase de vista y el documento actual.

En general, si usa los valores predeterminados de framework, puede omitir `CCreateContext`. Si intentas modificaciones más avanzadas, el código de origen de la biblioteca Microsoft Foundation Class o los programas de ejemplo, como VIEWEX, sirve de guía. Si olvida un parámetro necesario, una aserción de framework le indicará lo que olvidó.

Para obtener más información sobre `CCreateContext`, vea el ejemplo de MFC [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)
