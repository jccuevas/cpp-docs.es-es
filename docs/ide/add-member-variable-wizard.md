---
title: Agregar variables miembro | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.variable.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Member Variable Wizard [C++]
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3ae6a3aef4bdf774b5630a9bb0b2a0b49f7f29b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="add-member-variable-wizard"></a>Asistente para agregar variables miembro
Este asistente agrega una declaración de variable de miembro para el archivo de encabezado y, según las opciones, puede agregar código al archivo .cpp. Cuando haya agregado la variable miembro mediante el asistente, puede modificar el código en el entorno de desarrollo.  
  
 **Acceso**  
 Establece el acceso a la variable miembro. Modificadores de acceso son palabras clave que especifican el acceso que tienen otras clases a la variable miembro. Vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md) para obtener más información acerca de cómo especificar el acceso. El nivel de acceso a las variables de miembro se establece en **público** de forma predeterminada.  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 **Tipo de variable**  
 Establece el tipo de valor devuelto de la variable de miembro que se va a agregar.  
  
-   Si va a agregar una variable de miembro que no es un control de cuadro de diálogo, seleccione en la lista de tipos disponibles.  
  
     Para obtener información acerca de los tipos, vea [tipos fundamentales](../cpp/fundamental-types-cpp.md).  
  
    |||  
    |-|-|  
    |`char`|**short**|  
    |**double**|`unsigned char`|  
    |**float**|`unsigned int`|  
    |`int`|`unsigned long`|  
    |**long**||  
  
-   Si va a agregar una variable miembro para un control de cuadro de diálogo, este cuadro se rellena con el tipo de objeto devuelto para un control o un valor. Si selecciona **Control**, a continuación, **tipo de Variable** especifica la clase base del control que seleccione en la **Id. de Control** cuadro. Si el control de cuadro de diálogo puede contener un valor, y si se selecciona **valor**, a continuación, **tipo de Variable** especifica el tipo adecuado para el valor de dicho control puede contener. Vea [controles de cuadro de diálogo y tipos de Variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.  
  
     Este valor depende de la selección de **Id. de Control** y no se puede cambiar.  
  
 **Nombre de variable**  
 Establece el nombre de la variable de miembro que se va a agregar. Normalmente, variables de miembro comienzan con la cadena de identificación "m_", que se le proporcionará de forma predeterminada.  
  
 **Variable de control**  
 Indica que la variable miembro administra un control dentro de un cuadro de diálogo con [intercambio y validación de datos](../mfc/dialog-data-exchange-and-validation.md) admite. Vea [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) para obtener más información. Esta opción solo está disponible para las variables miembro agregadas a clases derivadas de [CDialog](../mfc/reference/cdialog-class.md). Active esta casilla para activar el **Id. de Control** y **tipo de Control** opciones.  
  
 **Id. de control**  
 Establece el identificador de la variable de control que se va a agregar. En la lista, seleccione el identificador para el tipo de control para el que va a agregar la variable miembro. La lista está activa solo cuando la **la variable de Control** casilla está activada y se limita a identificadores para los controles que se ha agregado al cuadro de diálogo. Por ejemplo, para el estándar **Aceptar** es el identificador del Control de botón, **IDOK**.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Control**|Esta opción se establece de forma predeterminada para el tipo de control. Administra el control de sí misma y no el estado o el contenido (como puede hacer con un cuadro de lista, un cuadro combinado o un cuadro de edición) del control.|  
|**Valor**|Esta opción está disponible únicamente para los tipos de control que pueden contener un valor (por ejemplo, un cuadro de edición) o reflejar un estado (por ejemplo, una casilla de verificación) y para el que se puede administrar el intervalo, contenido o su estado. Vea [controles de cuadro de diálogo y tipos de Variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.|  
  
 **Categoría**  
 Especifica si la variable se basa en un tipo de control o el valor del control.  
  
 **Tipo de control**  
 Establece el tipo de control que se va a agregar. Este cuadro no está disponible para cambiar. Por ejemplo, un botón tiene el tipo de control **botón**, y un cuadro combinado tiene el tipo de control **COMBOBOX**. Vea [controles de cuadro de diálogo y tipos de Variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.  
  
 **Número máximo de caracteres**  
 Disponible solo cuando **tipo de Variable** está establecido en [CString](../atl-mfc-shared/reference/cstringt-class.md). Indica el número máximo de caracteres que puede contener el control.  
  
 **Valor mínimo**  
 Sólo está disponible cuando el tipo de variable es **BOOL**, `int`, **UINT**, **largo**, `DWORD`, **float**, **doble**, **bytes**, **corto**, [COLECurrency](../mfc/reference/colecurrency-class.md) o [CTime](../atl-mfc-shared/reference/ctime-class.md). Indica el valor mínimo aceptable para una escala o intervalo de fechas.  
  
 **Valor de máximo**  
 Sólo está disponible cuando el tipo de variable es **BOOL**, `int`, **UINT**, **largo**, `DWORD`, **float**, **doble**, **bytes**, **corto**, `COLECurrency` o `CTime`. Indica el valor máximo aceptable para una escala o intervalo de fechas.  
  
 **archivo .h**  
 Para los controles de ActiveX, cuyas variables miembro requieren una clase contenedora. Establece el nombre del archivo de encabezado para agregar la declaración de clase.  
  
 **archivo .cpp**  
 Para los controles de ActiveX, cuyas variables miembro requieren una clase contenedora. Establece el nombre del archivo de implementación para agregar la definición de clase.  
  
 **Comentario**  
 Proporciona un comentario en el archivo de encabezado para la variable de miembro.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una Variable miembro](../ide/adding-a-member-variable-visual-cpp.md)