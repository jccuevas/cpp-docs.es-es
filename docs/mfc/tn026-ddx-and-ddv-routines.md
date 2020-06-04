---
title: 'TN026: Rutinas DDX y DDV'
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 711d433b51ca09836f372d09a11f86c28b82cce6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370344"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026: Rutinas DDX y DDV

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe la arquitectura de intercambio de datos de cuadro de diálogo (DDX) y validación de datos de cuadro de diálogo (DDV). También describe cómo escribir un procedimiento de DDX_ o DDV_ y cómo puede extender ClassWizard para usar sus rutinas.

## <a name="overview-of-dialog-data-exchange"></a>Descripción general del intercambio de datos de cuadro de diálogo

Todas las funciones de datos de diálogo se realizan con código C++. No hay recursos especiales ni macros mágicas. El corazón del mecanismo es una función virtual que se invalida en cada clase de cuadro de diálogo que realiza el intercambio y la validación de datos de cuadro de diálogo. Siempre se encuentra en esta forma:

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

Los comentarios AFX de formato especial permiten a ClassWizard localizar y editar el código dentro de esta función. El código que no es compatible con ClassWizard debe colocarse fuera de los comentarios de formato especial.

En el ejemplo \<anterior, data_exchange_function_call> tiene el formato:

```cpp
DDX_Custom(pDX, nIDC, field);
```

y \<data_validation_function_call> es opcional y tiene la forma:

```cpp
DDV_Custom(pDX, field, ...);
```

Se puede incluir más de un `DoDataExchange` par DDX_/DDV_ en cada función.

Consulte 'afxdd_.h' para obtener una lista de todas las rutinas de intercambio de datos de cuadro de diálogo y rutinas de validación de datos de cuadro de diálogo proporcionadas con MFC.

Los datos de diálogo son `CMyDialog` solo eso: datos de miembro en la clase. No se almacena en una estructura ni nada parecido.

## <a name="notes"></a>Notas

Aunque llamamos a esto "datos de diálogo", todas `CWnd` las entidades están disponibles en cualquier clase derivada de y no se limitan a solo diálogos.

Los valores iniciales de los datos se establecen en `//{{AFX_DATA_INIT` `//}}AFX_DATA_INIT` el constructor C++ estándar, normalmente en un bloque con y comentarios.

`CWnd::UpdateData`es la operación que realiza la inicialización y el control de errores alrededor de la llamada a `DoDataExchange`.

Puede llamar `CWnd::UpdateData` en cualquier momento para realizar el intercambio y la validación de datos. De `UpdateData`forma predeterminada (TRUE) `CDialog::OnOK` se `UpdateData`llama en el controlador `CDialog::OnInitDialog`predeterminado y (FALSE) se llama en el valor predeterminado .

La rutina DDV_ debe seguir inmediatamente la rutina DDX_ para ese *campo.*

## <a name="how-does-it-work"></a>Cómo funciona

No es necesario comprender lo siguiente para poder utilizar los datos de diálogo. Sin embargo, comprender cómo funciona esto en segundo plano le ayudará a escribir su propio procedimiento de intercambio o validación.

La `DoDataExchange` función miembro `Serialize` es muy similar a la función miembro - es responsable de obtener o establecer datos a/desde un formulario externo (en este caso controles en un cuadro de diálogo) desde/hacia los datos de miembro de la clase. El parámetro *pDX* es el contexto para realizar `CArchive` el `CObject::Serialize`intercambio de datos y es similar al parámetro a . El *pDX* `CDataExchange` (un objeto) tiene `CArchive` un indicador de dirección muy similar a como tiene un indicador de dirección:

- Si `!m_bSaveAndValidate`, a continuación, cargue el estado de datos en los controles.

- Si `m_bSaveAndValidate`, a continuación, establezca el estado de datos de los controles.

La validación `m_bSaveAndValidate` solo se produce cuando se establece. El valor `m_bSaveAndValidate` de viene determinado por `CWnd::UpdateData`el parámetro BOOL a .

Hay otros tres `CDataExchange` miembros interesantes:

- `m_pDlgWnd`: la ventana (normalmente un cuadro de diálogo) que contiene los controles. Esto es para evitar que los llamadores de la DDX_ y DDV_ funciones globales tengan que pasar 'esto' a cada rutina DDX/DDV.

- `PrepareCtrl`, `PrepareEditCtrl`y : Prepara un control de cuadro de diálogo para el intercambio de datos. Almacena el identificador de ese control para establecer el foco si se produce un error en una validación. `PrepareCtrl`se utiliza para controles `PrepareEditCtrl` que no son de edición y se utiliza para los controles de edición.

- `Fail`: Se llama después de abrir un cuadro de mensaje que alerta al usuario del error de entrada. Esta rutina restaurará el foco hasta el `PrepareCtrl` último `PrepareEditCtrl`control (la última llamada a o ) y producirá una excepción. Esta función miembro se puede llamar desde DDX_ y DDV_ rutinas.

## <a name="user-extensions"></a>Extensiones de usuario

Hay varias maneras de ampliar el mecanismo DDX/DDV predeterminado. Puede:

- Agregue nuevos tipos de datos.

    ```cpp
    CTime
    ```

- Agregue nuevos procedimientos de intercambio (DDX_).

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
    > ClassWizard no puede editar estas expresiones arbitrarias y, por lo tanto, deben moverse fuera de los comentarios de formato especial (//-AFX_DATA_MAP(CMyClass)).

Haga `DoDialogExchange` que la función miembro incluya condicionales o cualquier otra instrucción C++ válida con llamadas de función de validación y intercambio entre mezcladas.

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
> Como se muestra anteriormente, este código no puede ser editado por ClassWizard y debe usarse sólo fuera de los comentarios de formato especial.

## <a name="classwizard-support"></a>Soporte técnico de ClassWizard

ClassWizard admite un subconjunto de personalizaciones DDX/DDV al permitirle integrar sus propias rutinas DDX_ y DDV_ en la interfaz de usuario de ClassWizard. Hacer esto solo es beneficioso para el costo si planea reutilizar rutinas DDX y DDV particulares en un proyecto o en muchos proyectos.

Para ello, se realizan entradas especiales en DDX. CLW (versiones anteriores de Visual C++ almacenaba esta información en APSTUDIO. INI) o en el archivo . Archivo CLW. Las entradas especiales se pueden introducir en la sección [Información general] del proyecto. CLW o en la sección [ExtraDDX] del DDX. CLW en el directorio de archivos de programa de Microsoft Visual Studio Visual C++-bin. Es posible que deba crear el DDX. CLW si aún no existe. Si tiene previsto utilizar las rutinas de DDX_/DDV_ personalizadas solo en un proyecto determinado, agregue las entradas a la sección [Información general] del proyecto. CLW en su lugar. Si planea utilizar las rutinas en muchos proyectos, agregue las entradas a la sección [ExtraDDX] de DDX. Clw.

El formato general de estas entradas especiales es:

> ExtraDDXCount*n*

donde *n* es el número de ExtraDDX? líneas a seguir, de la forma

> ExtraDDX?-*teclas*; *vb-keys*; *prompt*; *tipo*; *initValue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *arg1* [; *prompt2*; *fmt2*]]

¿Dónde? es un número 1 - *n* que indica qué tipo DDX en la lista que se está definiendo.

Cada campo está delimitado por un carácter ';'. Los campos y su propósito se describen a continuación.

- *Llaves*

  Se permite una lista de caracteres individuales que indican para qué cuadro de diálogo controla este tipo de variable.

  |Carácter|Control permitido|
  |-|-|
  E | edición
  C | casilla de verificación de dos estados
  c | casilla de verificación de estado tri-estado
  R | primer botón de radio en un grupo
  L | cuadro de lista no ordenado
  l | cuadro de lista ordenado
  M | cuadro combinado (con elemento de edición)
  N | lista desplegable no ordenada
  n | lista de caída ordenada
  1 | si la inserción DDX se debe agregar a la cabecera de la lista (el valor predeterminado es agregar a la cola) Esto se utiliza generalmente para las rutinas DDX que transfieren la propiedad 'Control'.

- *vb-keys*

  Este campo solo se utiliza en el producto de 16 bits para controles VBX (los controles VBX no se admiten en el producto de 32 bits)

- *símbolo del sistema*

  Cadena para colocar en el cuadro combinado Propiedad (sin comillas)

- *type*

  Identificador único para que el tipo emita en el archivo de encabezado. En nuestro ejemplo anterior con DDX_Time, esto se establecería en CTime.

- *vb-keys*

  No se utiliza en esta versión y siempre debe estar vacío

- *initValue*

  Valor inicial — 0 o en blanco. Si está en blanco, no se escribirá ninguna línea de inicialización en la sección //-AFX_DATA_INIT del archivo de implementación. Se debe usar una entrada en blanco `CString`para `CTime`los objetos C++ (como , , , etc.) que tienen constructores que garantizan la inicialización correcta.

- *DDX_Proc*

  Identificador único para el procedimiento de DDX_. El nombre de la función C++ debe comenzar con "DDX_", pero no incluya "DDX_" en el \<identificador de> de DDX_Proc. En el ejemplo \<anterior, el identificador de> DDX_Proc sería Time. Cuando ClassWizard escribe la llamada de función en el archivo de implementación en la sección de AFX_DATA_MAP, anexa este nombre a DDX_, llegando así a DDX_Time.

- *Comentario*

  Comentario para mostrar en el cuadro de diálogo para la variable con este DDX. Coloque aquí cualquier texto que desee y, por lo general, proporcione algo que describa la operación realizada por el par DDX/DDV.

- *DDV_Proc*

  La parte DDV de la entrada es opcional. No todas las rutinas DDX tienen rutinas DDV correspondientes. A menudo, es más conveniente incluir la fase de validación como parte integral de la transferencia. Este suele ser el caso cuando la rutina DDV no requiere ningún parámetro, porque ClassWizard no admite rutinas DDV sin ningún parámetro.

- *Arg*

  Identificador único para el procedimiento de DDV_. El nombre de la función C++ debe comenzar con "DDV_", pero no incluya "DDX_" en el \<identificador de> DDX_Proc.

  *arg* es seguido por 1 o 2 DDV args:

  - *promptN*

      Cadena para colocar encima del elemento de edición (con & para el acelerador).

  - *fmtN*

      Formato de carácter para el tipo arg, uno de los:

      |Carácter|Tipo|
      |-|-|
      |d | int|
      |u | unsigned int|
      |D | long int (es decir, largo)|
      |U | largo sin firmar (es decir, DWORD)|
      |f | FLOAT|
      |F | double|
      |s | string|

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
