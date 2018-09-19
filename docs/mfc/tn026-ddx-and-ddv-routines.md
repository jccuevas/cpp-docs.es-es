---
title: 'TN026: Rutinas DDX y DDV | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DDX
- DDV
dev_langs:
- C++
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18377d423ab150773ef5438f39c8e74914b5c425
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317425"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026: Rutinas DDX y DDV

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe el intercambio de datos de cuadro de diálogo (DDX) y la arquitectura de validación (DDV) de datos de cuadro de diálogo. También se describe cómo escribir un procedimiento DDX_ o DDV_ y cómo puede ampliar ClassWizard para usar sus rutinas.

## <a name="overview-of-dialog-data-exchange"></a>Información general de intercambio de datos de cuadro de diálogo

Todas las funciones de datos de cuadro de diálogo ha terminado con el código de C++. No existen recursos especiales ni macros mágicas. El corazón del mecanismo es una función virtual que se invalide en cada clase de cuadro de diálogo que intercambian datos de cuadro de diálogo y la validación. Siempre se encuentra en este formulario:

```cpp
void CMyDialog::DoDataExchange(CDataExchange* pDX)
{
    CDialog::DoDataExchange(pDX);   // call base class

    //{{AFX_DATA_MAP(CMyDialog)
        <data_exchange_function_call>
        <data_validation_function_call>
    //}}AFX_DATA_MAP
}
```

Los comentarios de formato especial AFX permiten ClassWizard localizar y editar el código de esta función. Código que no es compatible con ClassWizard debe colocarse fuera de los comentarios de formato especiales.

En el ejemplo anterior, \<data_exchange_function_call > está en el formulario:

```cpp
DDX_Custom(pDX, nIDC, field);
```

y \<data_validation_function_call > es opcional y se encuentra en el formulario:

```cpp
DDV_Custom(pDX, field, ...);
```

Más de un par DDX_/DDV_ puede incluirse en cada `DoDataExchange` función.

Para obtener una lista de todas las rutinas de intercambio de datos de cuadro de diálogo y las rutinas de validación de datos de cuadros de diálogo proporcionadas por MFC, vea 'afxdd_.h'.

Datos de cuadro de diálogo están justamente eso: datos de miembro en el `CMyDialog` clase. No se almacena en un struct o algo similar.

## <a name="notes"></a>Notas

A pesar de que estos datos de cuadro de diálogo"", todas las características están disponibles en cualquier clase derivada de `CWnd` y no están limitados a sólo los cuadros de diálogo.

Los valores iniciales de los datos se establecen en el constructor de C++ estándar, por lo general en un bloque con `//{{AFX_DATA_INIT` y `//}}AFX_DATA_INIT` comentarios.

`CWnd::UpdateData` es la operación que realiza la inicialización y los errores en torno a la llamada a `DoDataExchange`.

Puede llamar a `CWnd::UpdateData` en cualquier momento para realizar el intercambio de datos y la validación. De forma predeterminada `UpdateData`(TRUE) se llama en el valor predeterminado `CDialog::OnOK` controlador y `UpdateData`(FALSE) que se llama en el valor predeterminado `CDialog::OnInitDialog`.

La rutina DDV_ debe seguir inmediatamente a la rutina DDX_ para que *campo*.

## <a name="how-does-it-work"></a>¿Cómo funciona

No es necesario entender los siguientes conceptos para poder usar datos de cuadro de diálogo. Sin embargo, comprender cómo funciona en segundo plano le ayudará a escribir su propio procedimiento de exchange o validación.

El `DoDataExchange` función miembro es muy similar a la `Serialize` la función miembro - es responsable de obtener o establecer los datos hacia y desde un formulario externo (en este caso se controla en un cuadro de diálogo) desde y hacia los datos de miembro de la clase. El *pDX* parámetro es el contexto para el intercambio de datos y es similar a la `CArchive` parámetro `CObject::Serialize`. El *pDX* (un `CDataExchange` objeto) tiene una dirección marca muy parecido al `CArchive` tiene una marca de dirección:

- Si `!m_bSaveAndValidate`, a continuación, cargar el estado de los datos en los controles.

- Si `m_bSaveAndValidate`, a continuación, establezca el estado de los datos de los controles.

La validación se produce sólo cuando `m_bSaveAndValidate` está establecido. El valor de `m_bSaveAndValidate` viene determinada por el parámetro de tipo BOOL `CWnd::UpdateData`.

Hay tres otras interesantes `CDataExchange` miembros:

- `m_pDlgWnd`: La ventana (normalmente un cuadro de diálogo) que contiene los controles. Esto es para evitar que los autores de llamadas de las funciones DDX_ y DDV_ globales de tener que pase 'this' todas las rutinas DDX/DDV.

- `PrepareCtrl`, y `PrepareEditCtrl`: prepara un control de cuadro de diálogo intercambio de datos. Almacena el identificador de ese control para establecer el foco si se produce un error en la validación. `PrepareCtrl` se utiliza para los controles que no sean edit y `PrepareEditCtrl` se usa para los controles de edición.

- `Fail`: Se le llama después de abrir un cuadro de mensaje que avisa al usuario los errores de entrada. Esta rutina restaurará el foco al último control (la última llamada a `PrepareCtrl` o `PrepareEditCtrl`) e inicia una excepción. Esta función miembro puede llamarse desde rutinas DDX_ y DDV_.

## <a name="user-extensions"></a>Extensiones de usuario

Hay varias maneras de extender el mecanismo DDX/DDV de forma predeterminada. Puede realizar lo siguiente:

- Agregar nuevos tipos de datos.

    ```cpp
    CTime
    ```

- Agregue nuevos procedimientos de exchange (DDX_).

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- Agregue nuevos procedimientos de validación (DDV_).

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- Pasar expresiones arbitrarias a los procedimientos de validación.

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > Estas expresiones arbitrarias ClassWizard no puede editar y, por tanto, se debe mover fuera de los comentarios de formato especiales (/ / {{AFX_DATA_MAP(CMyClass)).

Tiene la `DoDialogExchange` función miembro se incluyen instrucciones condicionales o cualquier otra instrucción de C++ válido con entremezclados llamadas de función de intercambio y validación.

```cpp
//{{AFX_DATA_MAP(CMyClass)
DDX_Check(pDX, IDC_SEX, m_bFemale);
DDX_Text(pDX, IDC_EDIT1, m_age);
//}}AFX_DATA_MAP
if (m_bFemale)
    DDV_MinMax(pDX, age, 0, m_maxFemaleAge);
else
    DDV_MinMax(pDX, age, 0, m_maxMaleAge);
```

> [!NOTE]
> Como se indicó anteriormente, dicho código ClassWizard no pueden editarlas y debe usarse solo fuera de los comentarios de formato especiales.

## <a name="classwizard-support"></a>Soporte técnico de ClassWizard

ClassWizard admite un subconjunto de las personalizaciones de DDX/DDV, ya que permite integrar sus propias rutinas DDX_ y DDV_ en la interfaz de usuario del Asistente para clases. Hacer esto es beneficioso único costo si piensa reutilizar rutinas DDX y DDV determinadas en un proyecto o en varios proyectos.

Para ello, se realizan entradas especiales en las DDX. CLW (las versiones anteriores de Visual C++ almacenan esta información en APSTUDIO. INI) o en el proyecto. Archivo CLW. Las entradas especiales pueden estar escrito en la sección [información General] de su proyecto. Archivo CLW o en la sección [ExtraDDX] de la DDX. Archivo CLW en el directorio de \Program Files\Microsoft Studio\Visual Visual C ++ \bin. Deberá crear la DDX. Archivo CLW si aún no existe. Si tiene previsto usar las rutinas DDX_/DDV_ personalizadas solo en un determinado proyecto, agregue las entradas a la sección [información General] del proyecto. CLW de archivo en su lugar. Si tiene previsto usar las rutinas en muchos proyectos, agregue las entradas a la sección [ExtraDDX] de DDX. CLW.

Es el formato general de estas entradas especiales:

> ExtraDDXCount =*n*

donde *n* es el número de ExtraDDX? las líneas que desea seguir el formato

> ExtraDDX? =*claves*; *vb claves*; *símbolo del sistema*; *tipo*; *initValue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *arg1* [; *prompt2*; *fmt2*]]

¿donde? es un número 1 - *n* que indica qué tipo DDX en la lista que se está definiendo.

Cada campo está delimitado por un carácter ';'. A continuación se describen los campos y su finalidad.

- *Claves*

  Una lista de caracteres individuales que se indica para qué controles de cuadro de diálogo se permite este tipo de variable.

  |Carácter|Control permitido|
  |-|-|
  E | editar
  C | casilla de verificación de dos Estados
  c | casilla de verificación de tres Estados
  R | primer botón de radio en un grupo
  L | cuadro de lista no ordenado
  l | cuadro de lista ordenada
  M | cuadro combinado (con un elemento de edición)
  N | lista desplegable no ordenado
  n | lista ordenada
  1 | Si la inserción DDX debe agregarse al encabezado de lista (predeterminada es agregar al final) se utiliza normalmente para rutinas DDX que transferir la propiedad 'Control'.

- *claves de VB*

  Este campo solo se usa en el producto de 16 bits para los controles VBX (no se admiten los controles VBX en el producto de 32 bits)

- *prompt*

  Cadena para colocar en el cuadro combinado de propiedades (sin comillas)

- *type*

  Identificador único de tipo emitir en el archivo de encabezado. En el ejemplo anterior con DDX_Time, se podría establecer en CTime.

- *claves de VB*

  No se usa en esta versión y siempre debe estar vacío

- *initValue*

  Valor inicial: 0 o en blanco. Si está en blanco, no se escribirá ninguna línea de inicialización en la sección //{{AFX_DATA_INIT del archivo de implementación. Se debe usar una entrada en blanco para los objetos de C++ (como `CString`, `CTime`, etc.) que tienen constructores que garantizan la inicialización correcta.

- *DDX_Proc*

  Identificador único para el procedimiento DDX_. El nombre de función de C++ debe empezar por "DDX_", pero no incluya "DDX_" en el \<DDX_Proc > identificador. En el ejemplo anterior, el \<DDX_Proc > identificador sería el tiempo. Cuando ClassWizard escribe la llamada de función en el archivo de implementación en el {{sección AFX_DATA_MAP, anexa este nombre a DDX_, así que llegan a DDX_Time.

- *comment*

  Comentario que se muestran en el cuadro de diálogo de la variable con este DDX. Coloque cualquier texto que le gustaría aquí y se suele proporcionar algo que describe la operación realizada por el par DDX/DDV.

- *DDV_Proc*

  La parte DDV de la entrada es opcional. No todas las rutinas DDX tienen rutinas DDV correspondientes. A menudo, resulta más conveniente incluir la fase de validación como parte integral de la transferencia. Esto sucede a menudo cuando la rutina DDV no requiere ningún parámetro, porque ClassWizard no admite las rutinas DDV sin ningún parámetro.

- *arg*

  Identificador único para el procedimiento DDV_. El nombre de función de C++ debe empezar por "DDV_", pero no incluya "DDX_" en el \<DDX_Proc > identificador.

  *arg* seguido de argumentos DDV 1 o 2:

   - *promptN*

     Cadena que se coloca encima del elemento de edición (con & de acelerador).

   - *fmtN*

     Carácter de formato para el tipo de argumento, uno de:

     |Carácter|Tipo|
     |-|-|
     d | int
     u | unsigned int
     D | long int (es decir, long)
     U | Long sin signo (es decir, DWORD)
     f | float
     F | double
     s | cadena

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)  
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)  
