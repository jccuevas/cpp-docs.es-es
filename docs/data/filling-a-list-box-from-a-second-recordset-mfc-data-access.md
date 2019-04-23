---
title: Llenar un cuadro de lista con datos de otro conjunto de registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, filling list boxes
- list boxes, filling from second recordset
- recordsets [C++], filling list boxes or combo boxes
- CComboBox class, filling object from second rowset
- ODBC recordsets [C++], filling list boxes or combo boxes
- combo boxes [C++], filling from second recordset
- CListCtrl class, filling from second recordset
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
ms.openlocfilehash: 9428f8a59dca021a1bd0e00a7970f4d19bab46be
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030508"
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>Llenar un cuadro de lista con datos de otro conjunto de registros (acceso a datos MFC)

De manera predeterminada, una vista de registros está asociada con un único objeto de conjunto de registros, cuyos campos se asignan a los controles de la vista de registros. En ocasiones, podría interesarle colocar un cuadro de lista o un control de cuadro combinado en la vista de registros y rellenarlo con valores de otro objeto de conjunto de registros. El usuario puede utilizar el cuadro de lista para seleccionar una nueva categoría de información para que se muestre en la vista de registros. Este tema explica cómo y cuándo hacerlo.

> [!TIP]
>  Tenga en cuenta que el proceso de llenar un cuadro combinado o un cuadro de lista desde un origen de datos puede ser lento. Tome precauciones para evitar llenar un control con un gran número de registros procedentes de un conjunto de registros.

El modelo de este tema consta de un conjunto de registros principal que llena los controles del formulario, y un conjunto de registros secundario que llena un cuadro de lista o un cuadro combinado. El hecho de seleccionar una cadena del cuadro de lista hace que el programa vuelva a consultar el conjunto de registros principal en función de lo que se haya seleccionado. El siguiente procedimiento utiliza un cuadro combinado, pero se aplica igualmente a un cuadro de lista.

#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>Cómo rellenar un cuadro combinado o un cuadro de lista con datos de otro conjunto de registros

1. Crear el objeto de conjunto de registros ([CRecordset](../mfc/reference/crecordset-class.md).

1. Obtener un puntero a la [CComboBox](../mfc/reference/ccombobox-class.md) objeto para el control de cuadro combinado.

1. Vacíe el cuadro combinado de cualquier contenido anterior.

1. Desplazarse por todos los registros del conjunto de registros, una llamada a [CComboBox:: AddString](../mfc/reference/ccombobox-class.md#addstring) para cada cadena del registro actual que desea agregar al cuadro combinado.

1. Inicialice la selección en el cuadro combinado.

```cpp
void CSectionForm::OnInitialUpdate()
{
    // ...

    // Fill the combo box with all of the courses
    CENROLLDoc* pDoc = GetDocument();
    if (!pDoc->m_courseSet.Open())
        return;

    // ...

    m_ctlCourseList.ResetContent();
    if (pDoc->m_courseSet.IsOpen())
    {
        while (!pDoc->m_courseSet.IsEOF() )
        {
            m_ctlCourseList.AddString(
                pDoc->m_courseSet.m_CourseID);
            pDoc->m_courseSet.MoveNext();
        }
    }
    m_ctlCourseList.SetCurSel(0);
}
```

Esta función utiliza otro conjunto de registros, `m_courseSet`, que contiene un registro para cada curso ofrecido y un control `CComboBox`, `m_ctlCourseList`, que se almacena en la clase de vista de registros.

Esta función obtiene `m_courseSet` del documento y lo abre. Después, vacía `m_ctlCourseList` y se desplaza a través de `m_courseSet`. Para cada registro, la función llama a la función miembro `AddString` del cuadro combinado para agregar el valor del identificador de curso desde el registro. Por último, el código establece la selección del cuadro combinado.

## <a name="see-also"></a>Vea también

[Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)