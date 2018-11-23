---
title: Agregar una variable miembro
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.variable
- vc.codewiz.variable.overview
helpviewer_keywords:
- member variables, adding
- member variables
- add member variable wizard [C++]
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
ms.openlocfilehash: 2a519c0606a7df6e0ce55997a055d78865afafbf
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694418"
---
# <a name="add-a-member-variable"></a>Agregar una variable miembro

Se puede agregar una variable miembro a una clase mediante la Vista de clases. Las variables miembro pueden ser para [intercambio y validación de datos](../mfc/dialog-data-exchange-and-validation.md), o bien pueden ser genéricas. El Asistente para agregar variables miembro se ha diseñado para tomar la información relevante y usarla para insertar elementos en los archivos de código fuente en las ubicaciones adecuadas. Una variable miembro se puede agregar desde el [Editor de cuadros de diálogo](../windows/dialog-editor.md) de la [Vista de recursos](../windows/resource-view-window.md), o bien desde la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
> Cuando diseñe e implemente un cuadro de diálogo, es posible que le resulte más eficaz usar el Editor de cuadros de diálogo para agregar los controles de cuadro de diálogo y luego implementar las variables miembro de los controles.

**Para agregar una variable miembro para un control de cuadro de diálogo en la Vista de recursos mediante el Asistente para agregar variables miembro:**

1. En la Vista de recursos, expanda el nodo del proyecto y el nodo Cuadro de diálogo para mostrar la lista de cuadros de diálogo del proyecto.

1. Haga doble clic en el cuadro de diálogo al que quiera agregar la variable miembro para abrirlo en el Editor de cuadros de diálogo.

1. En el cuadro de diálogo que se muestra en el Editor de cuadros de diálogo, haga clic con el botón derecho en el control al que quiera agregar la variable miembro.

1. En el menú contextual, elija **Agregar variable** para mostrar el [Asistente para agregar variables miembro](#add-member-variable-wizard).

   > [!NOTE]
   > Ya se proporciona un valor predeterminado en **Id. de control**.

1. Proporcione la información en los cuadros apropiados del asistente. Para obtener más información, vea [Tipos de controles de cuadro de diálogo y tipos de variable](#dialog-box-controls-and-variable-types).

1. Seleccione **Finalizar** para agregar la definición y el código de implementación al proyecto y cerrar el asistente.

**Para agregar una variable miembro desde la Vista de clases mediante el Asistente para agregar variables miembro:**

1. En la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code), expanda el nodo del proyecto para mostrar las clases del proyecto.

1. Haga clic con el botón derecho en la clase a la que quiera agregar una variable.

1. En el menú contextual, elija **Agregar** y luego **Agregar variable** para mostrar el Asistente para agregar variables miembro.

1. Proporcione la información en los cuadros apropiados del asistente. Para obtener más información, vea [Asistente para agregar variables miembro](#add-member-variable-wizard).

1. Seleccione **Finalizar** para agregar la definición y el código de implementación al proyecto y cerrar el asistente.

## <a name="in-this-section"></a>En esta sección

- [Asistente para agregar variables miembro](#add-member-variable-wizard)
- [Tipos de controles de cuadro de diálogo y tipos de variable](#dialog-box-controls-and-variable-types)

## <a name="add-member-variable-wizard"></a>Asistente para agregar variables miembro

Este asistente agrega una declaración de variable miembro al archivo de encabezado. Según las opciones, puede agregar código al archivo .cpp. Una vez agregada la variable miembro mediante el asistente, el código se puede modificar en el entorno de desarrollo.

- **Acceso**

  Establece el acceso a la variable miembro. Los modificadores de acceso son palabras clave que especifican el acceso que tienen otras clases a la variable miembro. Para obtener más información sobre la especificación de acceso, vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md). El nivel de acceso a las variables miembro se establece en `public` de forma predeterminada.

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

- **Tipo de variable**

  Establece el tipo de valor devuelto de la variable miembro que se va a agregar.

  - Si se va a agregar una variable miembro que no sea un control de cuadro de diálogo, seleccione en la lista de tipos disponibles.

    Para obtener información sobre los tipos, vea [Tipos fundamentales](../cpp/fundamental-types-cpp.md).

    |||
    |-|-|
    |`char`|`short`|
    |`double`|`unsigned char`|
    |`float`|`unsigned int`|
    |`int`|`unsigned long`|
    |`long`||

  - Si se va a agregar una variable miembro para un control de cuadro de diálogo, este cuadro se rellena con el tipo de objeto devuelto para un control o valor. Si se selecciona **Control**, **Tipo de variable** especifica la clase base del control que se seleccione en el cuadro **Id. de control**. Si el control de cuadro de diálogo puede contener un valor, y si se selecciona **Valor**, en **Tipo de variable** se especifica el tipo adecuado para el valor que puede contener ese control. Para obtener más información, vea [Tipos de controles de cuadro de diálogo y tipos de variable](#dialog-box-controls-and-variable-types).

    Este valor depende de la selección de **Id. de control** y no se puede cambiar.

- **Nombre de variable**

  Establece el nombre de la variable miembro que se va a agregar. Normalmente, las variables miembro comienzan con la cadena de identificación `m_`, que se proporciona de forma predeterminada.

- **Variable de control**

  Indica que la variable miembro administra un control dentro de un cuadro de diálogo con compatibilidad con el [intercambio y la validación de datos](../mfc/dialog-data-exchange-and-validation.md). Para obtener más información, vea [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange). Esta opción solo está disponible para las variables miembro que se agregan a las clases derivadas de [CDialog](../mfc/reference/cdialog-class.md). Active esta casilla para activar las opciones **Id. de control** y **Tipo de control**.

- **Id. de control**

  Establece el identificador de la variable de control que se va a agregar. En la lista, seleccione el identificador para el tipo de control para el que se va a agregar la variable miembro. La lista solo está activa cuando la casilla **Variable de control** está activada y se limita a los identificadores de los controles que ya se han agregado al cuadro de diálogo. Por ejemplo, para el botón **Aceptar** estándar, el id. de control es **IDOK**.

  |Opción|Descripción|
  |------------|-----------------|
  |**Control**|Esta opción se establece de forma predeterminada para el tipo de control. Administra el propio control y no el estado ni el contenido de este (como se podría querer administrar para un cuadro de lista, cuadro combinado o cuadro de edición).|
  |**Valor**|Esta opción está disponible para los tipos de control que pueden contener un valor o mostrar un estado, como un cuadro de edición o una casilla de verificación. También está disponible para los tipos de control cuyo intervalo, contenido o estado se podría administrar. Para obtener más información, vea [Tipos de controles de cuadro de diálogo y tipos de variable](#dialog-box-controls-and-variable-types).|

- **Categoría**

  Especifica si la variable se basa en el tipo de control o en el valor del control.

- **Tipo de control**

  Establece el tipo de control que se va a agregar. Este cuadro no se puede cambiar. Por ejemplo, un botón tiene el tipo de control **BUTTON**, y un cuadro combinado tiene el tipo de control **COMBOBOX**. Para obtener más información, vea [Tipos de controles de cuadro de diálogo y tipos de variable](#dialog-box-controls-and-variable-types).

- **Número máximo de caracteres**

  Disponible solo cuando **Tipo de variable** se establece en [CString](../atl-mfc-shared/reference/cstringt-class.md). Indica el número máximo de caracteres que puede contener el control.

- **Valor mínimo**

  Solo está disponible cuando el tipo de variable es `BOOL`, `int`, `UINT`, `long`, `DWORD`, `float`, `double`, `BYTE`, `short`, [COLECurrency](../mfc/reference/colecurrency-class.md) o [CTime](../atl-mfc-shared/reference/ctime-class.md). Indica el valor mínimo aceptable para una escala o intervalo de fechas.

- **Valor máximo**

  Solo está disponible cuando el tipo de variable es `BOOL`, `int`, `UINT`, `long`, `DWORD`, `float`, `double`, `BYTE`, `short`, `COLECurrency` o `CTime`. Indica el valor más alto aceptable para una escala o intervalo de fechas.

- **Archivo .h**

  Para los controles ActiveX, cuyas variables miembro requieren una clase contenedora. Establece el nombre del archivo de encabezado al que se va a agregar la declaración de clase.

- **Archivo .cpp**

  Para los controles ActiveX, cuyas variables miembro requieren una clase contenedora. Establece el nombre del archivo de implementación al que se va a agregar la declaración de clase.

- **Comentario**

  Proporciona un comentario en el archivo de encabezado para la variable miembro.

## <a name="dialog-box-controls-and-variable-types"></a>Tipos de controles de cuadro de diálogo y tipos de variable

Se puede usar el [Asistente para agregar variables miembro](#add-member-variable-wizard) para agregar una variable miembro a un control de cuadro de diálogo creado mediante MFC. El tipo de control para el que se agregue la variable miembro determina las opciones que aparecen en el cuadro de diálogo.

En la tabla siguiente se describen todos los tipos de control de cuadro de diálogo admitidos en MFC y el [Editor de cuadros de diálogo](../windows/dialog-editor.md). También se muestran sus tipos y valores disponibles.

|Control|Tipo de control|Tipo de variable de control|Tipo de variable de valor|Valores mínimos y máximos (solo tipo de valor)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|Animation (control)|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Ninguno; solo el control|N/D|
|Botón|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|Ninguno; solo el control|N/D|
|Casilla de verificación|CHECK|[CButton](../mfc/reference/cbutton-class.md)|`BOOL`|Valor máximo y mínimo|
|Cuadro combinado|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|Número máximo de caracteres|
|Control de selector de fecha y hora|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|Valor máximo y mínimo|
|Cuadro de edición|EDITAR|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime` o `COleCurrency`|Valor máximo y mínimo; algunos admiten número máximo de caracteres|
|Control de tecla de acceso rápido|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Ninguno; solo el control|N/D|
|Cuadro de lista|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|Número máximo de caracteres|
|List (control)|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|Ninguno; solo el control|N/D|
|Month Calendar (control)|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Valor máximo y mínimo|
|Control de progreso|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Ninguno; solo el control|N/D|
|Control de edición de texto enriquecido 2|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Número máximo de caracteres|
|Control de edición de texto enriquecido|RICHEDIT|`CRichEditCtrl`|`CString`|Número máximo de caracteres|
|Barra de desplazamiento (vertical u horizontal)|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Valor máximo y mínimo|
|Control deslizante|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Valor máximo y mínimo|
|Control de botón de número|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Ninguno; solo el control|N/D|
|Control Tab|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Ninguno; solo el control|N/D|
|Tree (control)|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Ninguno; solo el control|N/D|
