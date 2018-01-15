---
title: 'TN026: Rutinas DDX y DDV | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DDX
- DDV
dev_langs: C++
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15c2309e8080892bdca2753c1ea6128ce419862f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026: Rutinas DDX y DDV
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe el intercambio de datos de cuadros de diálogo (DDX) y la arquitectura de validación (DDV) de datos de cuadro de diálogo. También se describe cómo escribir un procedimiento DDX_ o DDV_ y cómo puede ampliarlo ClassWizard para usar sus rutinas.  
  
## <a name="overview-of-dialog-data-exchange"></a>Información general de intercambio de datos de cuadros de diálogo  
 Todas las funciones de datos de cuadro de diálogo se realizan con código de C++. No hay recursos especiales ni mágicas macros. El núcleo del mecanismo de es una función virtual que se invalide en cada clase de cuadro de diálogo que intercambian datos de cuadro de diálogo y la validación. Siempre se encuentra en este formato:  
  
```  
void CMyDialog::DoDataExchange(CDataExchange* pDX)  
{  
    CDialog::DoDataExchange(pDX);
*// call base class  
 *//{{AFX_DATA_MAP(CMyDialog)  
 <data_exchange_function_call>  
 <data_validation_function_call> *//}}AFX_DATA_MAP  
}  
```  
  
 Los comentarios de formato especiales AFX permiten ClassWizard localizar y editar el código dentro de esta función. Código que no es compatible con ClassWizard debe colocarse fuera de los comentarios de formato especiales.  
  
 En el ejemplo anterior, < data_exchange_function_call > tiene el formato:  
  
```  
DDX_Custom(pDX,
    nIDC,
    field);
```  
  
 y < data_validation_function_call > es opcional y se encuentra en el formulario:  
  
```  
DDV_Custom(pDX,
    field, ...);
```  
  
 Más de un par DDX_/DDV_ puede incluirse en cada `DoDataExchange` función.  
  
 Para obtener una lista de todas las rutinas de intercambio de datos de cuadros de diálogo y las rutinas de validación de datos de cuadros de diálogo proporcionadas por MFC, vea 'afxdd_.h'.  
  
 Datos de cuadro de diálogo están justamente eso: datos de miembro en el **CMyDialog, irá al** clase. No se almacena en un struct o algo similar.  
  
## <a name="notes"></a>Notas  
 Aunque se llama a estos datos de cuadro de diálogo de"", todas las características están disponibles en cualquier clase derivada de `CWnd` y no se limitan a los cuadros de diálogo solo.  
  
 Los valores iniciales de los datos se establecen en el constructor de C++ estándar, por lo general en un bloque con `//{{AFX_DATA_INIT` y `//}}AFX_DATA_INIT` comentarios.  
  
 `CWnd::UpdateData`es la operación que realiza la inicialización y el error control alrededor de la llamada a `DoDataExchange`.  
  
 Puede llamar a `CWnd::UpdateData` en cualquier momento para realizar el intercambio de datos y la validación. De forma predeterminada `UpdateData`(TRUE) se llama en el valor predeterminado `CDialog::OnOK` controlador y `UpdateData`(FALSE) se llama en el valor predeterminado `CDialog::OnInitDialog`.  
  
 La rutina DDV_ debe seguir inmediatamente a la rutina DDX_ para que *campo*.  
  
## <a name="how-does-it-work"></a>¿Cómo funciona  
 No es necesario entender los siguientes conceptos para utilizar datos de cuadro de diálogo. Sin embargo, entender cómo funciona en segundo plano le permitirá escribir su propio procedimiento de exchange o la validación.  
  
 El `DoDataExchange` función miembro es muy similar a la `Serialize` función miembro - es responsable de obtener o establecer datos hacia y desde un formulario externo (en este caso se controla en un cuadro de diálogo) y los datos de miembro de la clase. El `pDX` parámetro es el contexto para realizar el intercambio de datos y es similar a la `CArchive` parámetro `CObject::Serialize`. El `pDX` (un `CDataExchange` objeto) tiene una dirección de indicador muy parecido al `CArchive` tiene una marca de dirección:  
  
-   Si **! m_bSaveAndValidate**, a continuación, cargar el estado de los datos en los controles.  
  
-   Si `m_bSaveAndValidate`, a continuación, establezca el estado de los datos de los controles.  
  
 Validación solo se produce cuando `m_bSaveAndValidate` está establecido. El valor de `m_bSaveAndValidate` viene determinado por el parámetro de tipo BOOL `CWnd::UpdateData`.  
  
 Hay tres otros interesantes `CDataExchange` miembros:  
  
- `m_pDlgWnd`: La ventana (normalmente un cuadro de diálogo) que contiene los controles. Esto es para impedir que los llamadores de las funciones globales DDX_ y DDV_ tener que pasar 'this' en todas las rutinas DDX/DDV.  
  
- `PrepareCtrl`, y `PrepareEditCtrl`: prepara un control de cuadro de diálogo para el intercambio de datos. Almacena el identificador de ese control para establecer el foco si se produce un error en la validación. `PrepareCtrl`se utiliza para los controles de nonedit y `PrepareEditCtrl` se usa para controles de edición.  
  
- **Producirá un error en**: llama después de abrir un cuadro de mensaje al usuario los errores de entrada de alertas. Esta rutina restaurará el foco al último control (la última llamada a `PrepareCtrl` / `PrepareEditCtrl`) e inicia una excepción. Esta función miembro puede llamarse desde rutinas DDX_ y DDV_.  
  
## <a name="user-extensions"></a>Extensiones de usuario  
 Hay varias maneras de extender el mecanismo DDX/DDV de forma predeterminada. Puede realizar lo siguiente:  
  
-   Agregar nuevos tipos de datos.  
  
 ```  
    CTime 
 ```  
  
-   Agregar nuevos procedimientos de exchange (DDX_).  
  
 ```  
    void PASCAL DDX_Time(CDataExchange* pDX,
    int nIDC,
    CTime& tm);

 ```  
  
-   Agregar nuevos procedimientos de validación (DDV_).  
  
 ```  
    void PASCAL DDV_TimeFuture(CDataExchange* pDX,
    CTime tm,
    BOOL bFuture);
*// make sure time is in the future or past  
 ```  
  
-   Pasar expresiones arbitrarias a los procedimientos de validación.  
  
 ```  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxAge);

 ```  
  
    > [!NOTE]
    >  Estas expresiones arbitrarias ClassWizard no puede editar y, por tanto, se debe mover fuera de los comentarios de formato especiales (/ / {{AFX_DATA_MAP(CMyClass)).  
  
 Tiene la **DoDialogExchange** función miembro incluyen condicionales o cualquier otra instrucción de C++ válido con llamadas de función de intercambio y validación de mezclados.  
  
```  
//{{AFX_DATA_MAP(CMyClass)  
DDX_Check(pDX,
    IDC_SEX,
    m_bFemale);

DDX_Text(pDX,
    IDC_EDIT1,
    m_age);

//}}AFX_DATA_MAP  
if (m_bFemale)  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxFemaleAge);

else  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxMaleAge);
```  
  
> [!NOTE]
>  Tal y como se muestra arriba, este código no puede ser editado por ClassWizard y debe utilizarse solo fuera de los comentarios de formato especiales.  
  
## <a name="classwizard-support"></a>Compatibilidad de ClassWizard  
 ClassWizard admite un subconjunto de las personalizaciones de DDX/DDV por lo que le permite integrar sus propias rutinas DDX_ y DDV_ en la interfaz de usuario de ClassWizard. Esto resulta beneficioso único coste si piensa reutilizar rutinas DDX y DDV determinadas en un proyecto o en muchos proyectos.  
  
 Para ello, se realizan entradas especiales en DDX. CLW (las versiones anteriores de Visual C++ almacenan esta información en APSTUDIO. INI) o en el proyecto. Archivo CLW. Las entradas especial pueden ser especificado en la sección [información General] de su proyecto. Archivo CLW o en la sección [ExtraDDX] de la DDX. Archivo CLW en el directorio C ++ \bin \Program Studio\Visual Visual. Debe crear el DDX. Archivo CLW si aún no existe. Si planea usar las rutinas DDX_/DDV_ personalizadas sólo en un proyecto determinado, agregue las entradas a la sección [General Info] del proyecto. CLW de archivos en su lugar. Si tiene previsto usar las rutinas en muchos proyectos, agregue las entradas a la sección [ExtraDDX] de DDX. CLW.  
  
 Es el formato general de estas entradas especiales:  
  
```  
ExtraDDXCount=n  
```  
  
 donde n es el número de líneas de ExtraDDX seguir  
  
```  
ExtraDDX=<keys>;<vb-keys>; <prompt>; <type>; <initValue>; <DDX_Proc>  
[;<DDV_Proc>; <prompt1>; <arg1>; [<prompt2>; <fmt2>]]  
```  
  
 donde es un número 1 - n que indica qué tipo DDX en la lista que se está definiendo.  
  
 Cada campo está delimitado por un carácter ';'. A continuación se describen los campos y su finalidad.  
  
 \<claves >  
 = carácter único que indica para qué controles de cuadro de diálogo se permite este tipo de variable de la lista.  
  
 E = editar  
  
 C = la casilla de verificación de dos Estados  
  
 c = la casilla de verificación de tres Estados  
  
 R = primer botón de radio en un grupo  
  
 L = cuadro de lista no ordenado  
  
 l = cuadro de lista ordenada  
  
 M = cuadro combinado (con un elemento de edición)  
  
 N = lista desplegable no ordenado  
  
 n = lista ordenada  
  
 1 = si la inserción DDX debe agregarse al encabezado de lista (valor predeterminado se agrega al final) se utiliza normalmente para rutinas DDX que transferir la propiedad "Control".  
  
 \<claves de VB >  
 Este campo solo se usa en el producto de 16 bits para los controles VBX (VBX controles no se admiten en el producto de 32 bits)  
  
 \<símbolo del sistema >  
 Cadena que se coloca en el cuadro combinado de propiedad (sin comillas)  
  
 \<type>  
 Identificador único de tipo emitir en el archivo de encabezado. En nuestro ejemplo anterior con DDX_Time, esto debería establecerse en CTime.  
  
 \<claves de VB >  
 No se utiliza en esta versión y siempre debe estar vacío  
  
 \<initValue >  
 Valor inicial: 0 o en blanco. Si está en blanco, no hay ninguna línea de inicialización se escribirá en la sección //{{AFX_DATA_INIT del archivo de implementación. Se debe usar una entrada en blanco para objetos de C++ (como `CString`, `CTime`, y así sucesivamente) que tienen constructores que garantizan una inicialización correcta.  
  
 < DDX_Proc >  
 Identificador único para el procedimiento DDX_. El nombre de la función de C++ debe empezar por "DDX_", pero no incluyen "DDX_" en el identificador de < DDX_Proc >. En el ejemplo anterior, el identificador de < DDX_Proc > sería tiempo. Cuando ClassWizard escribe la llamada de función en el archivo de implementación en el {{sección AFX_DATA_MAP, que se anexe este nombre al DDX_, así que llegan a DDX_Time.  
  
 \<comentario >  
 Comentario que se mostrarán en el cuadro de diálogo para la variable con este DDX. Colocar cualquier texto que le gustaría aquí y se suele proporcionar algo que describe la operación realizada por el par DDX/DDV.  
  
 < DDV_Proc >  
 La parte DDV de la entrada es opcional. No todas las rutinas DDX tienen rutinas de DDV correspondientes. A menudo, es más conveniente incluir la fase de validación como parte integral de la transferencia. Esto suele ocurrir cuando la rutina DDV no requiere ningún parámetro, porque ClassWizard no admite las rutinas DDV sin ningún parámetro.  
  
 \<arg >  
 Identificador único para el procedimiento DDV_. El nombre de la función de C++ debe empezar por "DDV_", pero no incluyen "DDX_" en el identificador de < DDX_Proc >.  
  
 seguido de argumentos DDV 1 ó 2:  
  
 \<promptX >  
 cadena que se coloca encima del elemento de edición (con & de acelerador)  
  
 \<fmtX >  
 carácter de formato para el tipo de argumentos, uno de  
  
 d. = int  
  
 u = sin signo  
  
 D. = long int (es decir, long)  
  
 U = long sin signo (es decir, DWORD)  
  
 f = float  
  
 F = double  
  
 s = cadena  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

