---
title: "Asistente para agregar variables miembro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.variable.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para agregar variables miembro [C++]"
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Asistente para agregar variables miembro
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El asistente agrega una declaración de variable miembro al archivo de encabezado y, dependiendo de las opciones, puede agregar código al archivo .cpp.  Una vez agregada la variable miembro mediante el asistente, se puede modificar el código en el entorno de desarrollo.  
  
 **Acceso**  
 Establece el tipo de acceso a la variable miembro.  Los modificadores de acceso son palabras clave que especifican el acceso de otras clases a la variable miembro.  Vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md) para obtener más información sobre cómo especificar el acceso.  De forma predeterminada, el nivel de acceso a las variables miembro está establecido en **public**.  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 **Tipo de variable**  
 Establece el tipo de valor devuelto de la variable miembro que se está agregando.  
  
-   Si se está agregando una variable miembro que no es un control de cuadro de diálogo, selecciónela en la lista de tipos disponibles.  
  
     Para obtener información acerca de los tipos, vea [Tipos fundamentales](../cpp/fundamental-types-cpp.md).  
  
    |||  
    |-|-|  
    |`char`|**short**|  
    |**double**|`unsigned char`|  
    |**float**|`unsigned int`|  
    |`int`|`unsigned long`|  
    |**long**||  
  
-   Si está agregando una variable miembro que corresponde a un control de cuadro de diálogo, este cuadro aparece rellenado con el tipo de objeto devuelto para un control o valor.  Si selecciona **Control**, el dato **Tipo de variable** especifica la clase base del control que seleccione en el cuadro **Id. de control**.  Si el control de cuadro de diálogo puede contener un valor y selecciona **Valor**, **Tipo de variable** especifica el tipo correspondiente al valor que dicho control puede contener.  Vea [Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.  
  
     Este valor depende de lo seleccionado en **Id. de control** y no puede modificarse.  
  
 **Nombre de variable**  
 Establece el nombre de la variable miembro que se está agregando.  Las variables miembro suelen comenzar con la cadena de identificación "m\_", que se proporciona de forma predeterminada.  
  
 **Variable del control**  
 Indica que la variable miembro administra un control perteneciente a un cuadro de diálogo compatible con el [intercambio y validación de datos](../mfc/dialog-data-exchange-and-validation.md).  Vea [DoDataExchange](../Topic/CWnd::DoDataExchange.md) para obtener más información.  Esta opción sólo está disponible para las variables miembro agregadas a clases derivadas de [CDialog](../mfc/reference/cdialog-class.md).  Active esta casilla para activar las opciones **Id. de control** y **Tipo de control**.  
  
 **Id. de control**  
 Establece el identificador de la variable de control que se está agregando.  Seleccione el identificador de la lista que corresponda al tipo de control al cual está agregando la variable miembro.  La lista sólo está activa cuando está activada la casilla **Variable de control**, y está limitada a los ids. correspondientes a los controles que ya están agregados al cuadro de diálogo.  Por ejemplo, para el botón estándar **Aceptar**, el identificador de control es **IDOK**.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Control**|Esta opción está establecida de forma predeterminada para el tipo de control.  Administra el control como tal y no su estado o contenido \(como podemos hacer con un cuadro de lista, un cuadro combinado o un cuadro de edición\).|  
|**Valor**|Esta opción sólo está disponible para los tipos de control que pueden contener un valor \(como un cuadro de edición\) o reflejar un estado \(como una casilla\), y para los cuales se puede administrar el intervalo, el contenido o su estado.  Vea [Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.|  
  
 **Categoría**  
 Especifica si la variable se basa en un tipo de control o en el valor del control.  
  
 **Tipo de control**  
 Establece el tipo de control que se va a agregar.  Este cuadro no está disponible para realizar cambios.  Por ejemplo, un botón tiene el tipo de control **BUTTON**, y un cuadro combinado tiene el tipo **COMBOBOX.** Vea [Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.  
  
 **Número máximo de caracteres**  
 Sólo se encuentra disponible cuando **Tipo de variable** está establecido en [CString](../atl-mfc-shared/reference/cstringt-class.md).  Indica el número máximo de caracteres que puede contener el control.  
  
 **Valor mínimo**  
 Sólo se encuentra disponible cuando el tipo de variable es **BOOL**, `int`, **UINT**, **long**, `DWORD`, **float**, **double**, **BYTE**, **short**, [COLECurrency](../mfc/reference/colecurrency-class.md) o [CTime](../atl-mfc-shared/reference/ctime-class.md).  Indica el valor más pequeño aceptable para una escala o intervalo de fechas.  
  
 **Valor máximo**  
 Sólo se encuentra disponible cuando el tipo de variable es **BOOL**, `int`, **UINT**, **long**, `DWORD`, **float**, **double**, **BYTE**, **short**, `COLECurrency` o `CTime`.  Indica el valor más alto aceptable para una escala o intervalo de fechas.  
  
 **Archivo .H**  
 Para los controles ActiveX, cuyas variables miembro requieren una clase contenedora.  Establece el nombre del archivo de encabezado para agregar la declaración de clase.  
  
 **Archivo .cpp**  
 Para los controles ActiveX, cuyas variables miembro requieren una clase contenedora.  Establece el nombre del archivo de implementación para agregar la definición de clase.  
  
 **Comentarios**  
 Proporciona un comentario en el archivo de encabezado para la variable miembro.  
  
## Vea también  
 [Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)