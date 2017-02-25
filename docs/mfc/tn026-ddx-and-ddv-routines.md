---
title: "TN026: Rutinas DDX y DDV | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DDX"
  - "DDV"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DDV (validación de datos de cuadro de diálogo), procedimientos"
  - "DDX (intercambio de datos de cuadros de diálogo), procedimientos"
  - "TN026"
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN026: Rutinas DDX y DDV
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe el diálogo arquitectura de \(DDV\) de validación de datos de intercambio de datos \(DDX\) y de cuadro de diálogo.  También describe cómo escribe un procedimiento de DDX\_ o de DDV\_ y cómo extender ClassWizard para utilizar las rutinas.  
  
## Información general de diálogo Data Exchange  
 Todas las funciones de datos de cuadro de diálogo se hace con el código de C\+\+.  No hay recursos especiales o macros mágicas.  El núcleo del mecanismo es una función virtual que se invalida en cada clase de diálogo que haga el diálogo de intercambio y validación.  Se encuentra siempre en este formulario:  
  
```  
void CMyDialog::DoDataExchange(CDataExchange* pDX)  
{  
    CDialog::DoDataExchange(pDX);    // call base class  
  
    //{{AFX_DATA_MAP(CMyDialog)  
        <data_exchange_function_call>  
        <data_validation_function_call>  
    //}}AFX_DATA_MAP  
}  
```  
  
 Los comentarios especiales de AFX de formato permiten que ClassWizard busque y editar el código en esta función.  El código que no es compatible con ClassWizard debe colocarse fuera de los comentarios especiales de formato.  
  
 En el ejemplo anterior, \<el data\_exchange\_function\_call\> está en el formulario:  
  
```  
DDX_Custom(pDX, nIDC, field);  
```  
  
 y \<el data\_validation\_function\_call\> es opcional y se encuentra en el formulario:  
  
```  
DDV_Custom(pDX, field, ...);  
```  
  
 Más de un par de DDX\_\/DDV\_ se puede incluir en cada función de `DoDataExchange` .  
  
 Vea “afxdd\_.h” para una lista de todas las rutinas de intercambio de datos de cuadro de diálogo y de rutinas de validación de datos de diálogo proporcionadas MFC.  
  
 Los datos del diálogo es simplemente que: datos de miembros en la clase de **CMyDialog** .  No se almacena en un struct o nada similar.  
  
## Notas  
 Aunque denominemos este “datos de diálogo”, todas las características disponibles en cualquier clase derivada de `CWnd` y no se limitan solo los diálogos.  
  
 Los valores iniciales de datos se establecen en el constructor estándar de C\+\+, normalmente en un bloque con `//{{AFX_DATA_INIT` y comentarios de `//}}AFX_DATA_INIT` .  
  
 `CWnd::UpdateData` es la operación que realiza la inicialización y el control de errores alrededor de la llamada a `DoDataExchange`.  
  
 Puede llamar a `CWnd::UpdateData` en cualquier momento para realizar de intercambio y validación.  De forma predeterminada `UpdateData`\(TRUE\) se llama al controlador predeterminado y `UpdateData`\(FALSE\) de `CDialog::OnOK` se denomina en `CDialog::OnInitDialog`predeterminado.  
  
 La rutina de DDV\_ debe seguir inmediatamente a la rutina de DDX\_ para ese *campo*.  
  
## ¿Cómo funciona?  
 No necesita comprender lo siguiente para utilizar datos de diálogo.  Sin embargo, entender el funcionamiento de ésta en segundo plano le ayudará a escribir el propio procedimiento de intercambio o de validación.  
  
 La función miembro de `DoDataExchange` es como la función miembro de `Serialize` \- es responsable de obtener o establecer datos a y desde un formulario externo \(en este caso controles en un cuadro de diálogo\) from\/to datos de miembros en la clase.  El parámetro de `pDX` es el contexto para hacer de intercambio y es similar al parámetro de `CArchive` a `CObject::Serialize`.  `pDX` \(un objeto de `CDataExchange` \) tiene una dirección que el mensaje como `CArchive` tiene un indicador de la dirección:  
  
-   Si **\!m\_bSaveAndValidate**, entonces carga el estado de los datos de los controles.  
  
-   Si `m_bSaveAndValidate`, entonces establece el estado de los controles.  
  
 La validación se produce cuando se establece `m_bSaveAndValidate` .  El valor de `m_bSaveAndValidate` viene determinado por el parámetro de BOOL a `CWnd::UpdateData`.  
  
 Hay tres otros miembros interesantes de `CDataExchange` :  
  
-   `m_pDlgWnd`: La ventana \(normalmente un diálogo\) que contiene los controles.  Así se evita que los llamadores de funciones globales de DDX\_ y de DDV\_ tengan que pasar “this” a cada rutina de DDX\/DDV.  
  
-   `PrepareCtrl`, y `PrepareEditCtrl`: Prepara un control de cuadro de diálogo para el intercambio de datos.  Almacena el identificador de control para establecer el foco si se produce un error de validación.  `PrepareCtrl` se utiliza para los controles de nonedit y `PrepareEditCtrl` se utiliza para los controles de edición.  
  
-   **Con errores**: Se llama después de introducir para buscar un cuadro de mensaje que avisa al usuario al error de entrada.  Esta rutina restablecerá el foco al último control \(la última llamada a `PrepareCtrl`\/`PrepareEditCtrl`\) y producirá una excepción.  Esta función miembro se puede llamar desde las rutinas de DDX\_ y de DDV\_.  
  
## Extensiones de usuario  
 Hay varias maneras de extender el mecanismo predeterminado DDX\/DDV.  Puede realizar lo siguiente:  
  
-   Agregue nuevos tipos de datos.  
  
    ```  
    CTime  
    ```  
  
-   Agregue nuevos procedimientos de intercambio \(DDX\_???\).  
  
    ```  
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);  
    ```  
  
-   Agregue nuevos procedimientos de validación \(DDV\_???\).  
  
    ```  
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);  
    // make sure time is in the future or past  
    ```  
  
-   Pase las expresiones arbitrarias a los procedimientos de validación.  
  
    ```  
    DDV_MinMax(pDX, age, 0, m_maxAge);  
    ```  
  
    > [!NOTE]
    >  Tales expresiones arbitrarias no se pueden editar por ClassWizard y por tanto no se deben ir fuera de los comentarios especiales de formato \(\/{{AFX\_DATA\_MAP \(CMyClass\)\).  
  
 Tiene los condicionantes de la función miembro de **DoDialogExchange** o cualquier otra instrucción válida de C\+\+ con llamadas de función entremezcladas de intercambio y validación.  
  
```  
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
>  Como se indicó anteriormente, este código no se puede editar por ClassWizard y solo se debería usar fuera de los comentarios especiales de formato.  
  
## Compatibilidad de ClassWizard  
 ClassWizard admite un subconjunto de personalizaciones de DDX\/DDV que permite integrar dispone de las rutinas de DDX\_ y de DDV\_ en la interfaz de usuario de ClassWizard.  Ello se pendiente sólo beneficioso si piensa reutilizar rutinas determinadas de DDX y de DDV en un proyecto o en muchos proyectos.  
  
 Para ello, las entradas especiales se crean en DDX.CLW \(versiones anteriores de Visual C\+\+ almacenan esta información en APSTUDIO.INI\) o en el archivo de .CLW del proyecto.  Las entradas especiales se pueden entrar en la sección \[de información general\] del archivo de .CLW del proyecto o en la sección \[de ExtraDDX\] del archivo de DDX.CLW en el directorio de Files\\Microsoft Visual Studio\\Visual C\+\+\\bin de \\Program.  Puede que tenga que crear el archivo de DDX.CLW si no existe.  Si piensa utilizar las rutinas de personalizadas DDX\_\/DDV\_ sólo en un proyecto, agregue entradas a la sección \[de información general\] del archivo de proyecto .CLW en su lugar.  Si piensa utilizar las rutinas en muchos proyectos, agregue entradas a la sección de \[ExtraDDX\] de DDX.CLW.  
  
 El formato general de estas entradas especiales es:  
  
```  
ExtraDDXCount=n  
```  
  
 ¿dónde n es el número de ExtraDDX? líneas a seguir  
  
```  
ExtraDDX?=<keys>;<vb-keys>; <prompt>; <type>; <initValue>; <DDX_Proc>  
[;<DDV_Proc>; <prompt1>; <arg1>; [<prompt2>; <fmt2>]]  
```  
  
 ¿dónde? es un número 1 – indicación de n qué DDX escriba en la lista que se está definiendo.  
  
 Cada campo está delimitado por “; ” carácter.  Los campos y su finalidad se describen a continuación.  
  
 \<claves\>  
 \= la lista de caracteres individuales que indican para qué diálogo controla este tipo de la variable está permitido.  
  
 E \= edición  
  
 C \= casilla de la dos\- provincia  
  
 c \= control checkbox estado  
  
 R \= primero botón de radio de un grupo  
  
 L \= cuadro de lista nonsorted  
  
 l \= cuadro de lista ordenada  
  
 M \= cuadro combinado \(con el elemento de edición\)  
  
 N \= lista nonsorted de entrega  
  
 n \= lista ordenada de entrega  
  
 es 1 \= si la inserción de DDX se agrega al principio de la lista \(valor predeterminado agrega a la cola\) De se utiliza normalmente para las rutinas de DDX que transfiere la propiedad “Control”.  
  
 \<VB\-teclas\>  
 Este campo se utiliza en el producto de 16 bits para los controles de VBX \(controles de VBX no se admiten en el producto de 32 bits\)  
  
 \<indicador\>  
 Cadena en el lugar del cuadro combinado de la propiedad \(ninguna comillas\)  
  
 \<tipo\>  
 Elija el identificador para que el tipo emita en el archivo de encabezado.  En nuestro ejemplo anterior con DDX\_Time, esto se establecería a CTime.  
  
 \<VB\-teclas\>  
 No se utiliza en esta versión y siempre debe estar vacío  
  
 \<initValue\>  
 Valor inicial — 0 o espacio en blanco.  Si está en blanco, no se escribe ninguna línea de inicialización en \/\/{{sección de AFX\_DATA\_INIT del archivo de implementación.  Una entrada en blanco se debe utilizar para los objetos de C\+\+ \(como `CString`, `CTime`, etc.\) que tienen constructores que garantiza la inicialización correcta.  
  
 \<DDX\_Proc\>  
 Único identificador para el procedimiento de DDX\_.  El nombre de función de C\+\+ debe comenzar con “DDX\_”, pero no incluye “DDX\_” en \<el identificador\> de DDX\_Proc.  En el ejemplo anterior, \<el identificador\> de DDX\_Proc sería tiempo.  Cuando ClassWizard escribe la llamada de función en el archivo de implementación en {{sección de AFX\_DATA\_MAP, anexa este nombre a DDX\_, lo protege DDX\_Time.  
  
 \<comentario\>  
 Esto para mostrar en el cuadro de diálogo para la variable con este DDX.  Coloque el texto que desee aquí, y proporcionan normalmente algo que describe la operación realizada por pares de DDX\/DDV.  
  
 \<DDV\_Proc\>  
 La parte de DDV de entrada es opcional.  No todas las rutinas de DDX cuentan con las rutinas de DDV.  A menudo, es más conveniente incluir la fase de validación como parte integral de la transferencia.  Éste suele ser el caso si la rutina de DDV no requiere parámetros, porque Pero no admite las rutinas de DDV sin ningún parámetro.  
  
 \<argumento\>  
 Único identificador para el procedimiento de DDV\_.  El nombre de función de C\+\+ debe comenzar con “DDV\_”, pero no incluye “DDX\_” en \<el identificador\> de DDX\_Proc.  
  
 seguido de 1 o 2 args de DDV:  
  
 \<promptX\>  
 cadena el lugar sobre el elemento de edición \(con & para el acelerador\)  
  
 \<fmtX\>  
 carácter de formato para el tipo de argumento, uno de  
  
 d \= int  
  
 u \= sin signo  
  
 D \= long int \(es decir,\)  
  
 U \= de unsigned long \(es decir, DWORD\)  
  
 f \= float  
  
 F \= doble  
  
 s \= cadena  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)