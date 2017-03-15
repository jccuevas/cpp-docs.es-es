---
title: "Llenar un cuadro de lista con datos de otro conjunto de registros (acceso a datos MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComboBox (clase), rellenar un objeto con datos de otro conjunto de filas"
  - "CListCtrl (clase), rellenar con datos de otro conjunto de registros"
  - "cuadros combinados [C++], rellenar con datos de otro conjunto de registros"
  - "conjuntos de registros DAO"
  - "conjuntos de registros DAO, rellenar cuadros de lista o cuadros combinados"
  - "rellenar listas o cuadros combinados"
  - "cuadros de lista, rellenar con datos de otro conjunto de registros"
  - "varios conjuntos de registros en vistas de registros"
  - "conjuntos de registros ODBC [C++], rellenar cuadros de lista o cuadros combinados"
  - "vistas de registros, rellenar cuadros de lista"
  - "conjuntos de registros [C++], rellenar cuadros de lista o cuadros combinados"
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Llenar un cuadro de lista con datos de otro conjunto de registros (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

De manera predeterminada, una vista de registros está asociada con un único objeto de conjunto de registros, cuyos campos se asignan a los controles de la vista de registros.  En ocasiones, podría interesarle colocar un cuadro de lista o un control de cuadro combinado en la vista de registros y rellenarlo con valores de otro objeto de conjunto de registros.  El usuario puede utilizar el cuadro de lista para seleccionar una nueva categoría de información para que se muestre en la vista de registros.  Este tema explica cómo y cuándo hacerlo.  
  
> [!TIP]
>  Tenga en cuenta que el proceso de llenar un cuadro combinado o un cuadro de lista desde un origen de datos puede ser lento.  Tome precauciones para evitar llenar un control con un gran número de registros procedentes de un conjunto de registros.  
  
 El modelo de este tema consta de un conjunto de registros principal que llena los controles del formulario, y un conjunto de registros secundario que llena un cuadro de lista o un cuadro combinado.  El hecho de seleccionar una cadena del cuadro de lista hace que el programa vuelva a consultar el conjunto de registros principal en función de lo que se haya seleccionado.  El siguiente procedimiento utiliza un cuadro combinado, pero se aplica igualmente a un cuadro de lista.  
  
#### Cómo rellenar un cuadro combinado o un cuadro de lista con datos de otro conjunto de registros  
  
1.  Cree el objeto de conjunto de registros \([CRecordset](../mfc/reference/crecordset-class.md) para ODBC, [CDaoRecordset](../mfc/reference/cdaorecordset-class.md) para DAO\).  
  
2.  Obtenga un puntero al objeto [CComboBox](../mfc/reference/ccombobox-class.md) para el control de cuadro combinado.  
  
3.  Vacíe el cuadro combinado de cualquier contenido anterior.  
  
4.  Desplácese por todos los registros del conjunto de registros, llamando a [CComboBox::AddString](../Topic/CComboBox::AddString.md) para cada cadena del registro actual que desee agregar al cuadro combinado.  
  
5.  Inicialice la selección en el cuadro combinado.  
  
```  
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
  
 Esta función obtiene `m_courseSet` del documento y lo abre.  Después, vacía `m_ctlCourseList` y se desplaza a través de `m_courseSet`.  Para cada registro, la función llama a la función miembro `AddString` del cuadro combinado para agregar el valor del identificador de curso desde el registro.  Por último, el código establece la selección del cuadro combinado.  
  
## Vea también  
 [Vistas de registros \(acceso a datos MFC\)](../data/record-views-mfc-data-access.md)   
 [Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)