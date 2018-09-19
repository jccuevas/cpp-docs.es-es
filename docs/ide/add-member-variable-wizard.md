---
title: Asistente para agregar variables miembro | Microsoft Docs
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
ms.openlocfilehash: 4d4518a48d51e6187015dc3fd7b5456e04e1ae84
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701537"
---
# <a name="add-member-variable-wizard"></a>Asistente para agregar variables miembro
Este asistente agrega una declaración de variable miembro al archivo de encabezado y, según las opciones, puede agregar código al archivo .cpp. Una vez agregada la variable miembro mediante el asistente, el código se puede modificar en el entorno de desarrollo.  
  
- **Acceso**

   Establece el acceso a la variable miembro. Los modificadores de acceso son palabras clave que especifican el acceso que tienen otras clases a la variable miembro. Vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md) para obtener más información sobre cómo especificar el acceso. El nivel de acceso a las variables miembro se establece en **public** de forma predeterminada.  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
- **Tipo de variable**

   Establece el tipo de valor devuelto de la variable miembro que se va a agregar.  
  
   - Si se va a agregar una variable miembro que no es un control de cuadro de diálogo, seleccione en la lista de tipos disponibles.  
  
      Para obtener información sobre los tipos, vea [Tipos fundamentales](../cpp/fundamental-types-cpp.md).  
  
      |||  
      |-|-|  
      |**char**|**short**|  
      |**double**|**unsigned char**|  
      |**float**|**unsigned int**|  
      |**int**|**unsigned long**|  
      |**long**||  
  
   - Si se va a agregar una variable miembro para un control de cuadro de diálogo, este cuadro se rellena con el tipo de objeto devuelto para un control o un valor. Si se selecciona **Control**, **Tipo de variable** especifica la clase base del control que se seleccione en el cuadro **Id. de control**. Si el control de cuadro de diálogo puede contener un valor, y si se selecciona **Valor**, en **Tipo de variable** se especifica el tipo adecuado para el valor que puede contener ese control. Vea [Controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.  
  
      Este valor depende de la selección de **Id. de control** y no se puede cambiar.  
  
- **Nombre de variable**

   Establece el nombre de la variable miembro que se va a agregar. Normalmente, las variables miembro comienzan con la cadena de identificación "m_", que se proporciona de forma predeterminada.  
  
- **Variable de control**

   Indica que la variable miembro administra un control dentro de un cuadro de diálogo con compatibilidad con el [intercambio y la validación de datos](../mfc/dialog-data-exchange-and-validation.md). Vea [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) para obtener más información. Esta opción solo está disponible para las variables miembro que se agregan a las clases derivadas de [CDialog](../mfc/reference/cdialog-class.md). Active esta casilla para activar las opciones **Id. de control** y **Tipo de control**.  
  
- **Id. de control**

   Establece el identificador de la variable de control que se va a agregar. En la lista, seleccione el identificador para el tipo de control para el que se va a agregar la variable miembro. La lista solo está activa cuando la casilla **Variable de control** está activada y se limita a los identificadores de los controles que ya se han agregado al cuadro de diálogo. Por ejemplo, para el botón **Aceptar** estándar, el id. de control es **IDOK**.  
  
   |Opción|Descripción|  
   |------------|-----------------|  
   |**Control**|Esta opción se establece de forma predeterminada para el tipo de control. Administra el propio control y no el estado ni el contenido (como se podría hacer con un cuadro de lista, cuadro combinado o cuadro de edición) del control.|  
   |**Valor**|Esta opción solo está disponible para los tipos de control que pueden contener un valor (por ejemplo, un cuadro de edición) o que reflejan un estado (por ejemplo, una casilla) y para los que es posible que administre el intervalo, el contenido o el estado. Vea [Controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.|  
  
- **Categoría**

   Especifica si la variable se basa en el tipo de control o en el valor del control.  
  
- **Tipo de control**

   Establece el tipo de control que se va a agregar. Este cuadro no está disponible para cambiar. Por ejemplo, un botón tiene el tipo de control **BUTTON**, y un cuadro combinado tiene el tipo de control **COMBOBOX**. Vea [Controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.  
  
- **Número máximo de caracteres**

   Disponible solo cuando **Tipo de variable** se establece en [CString](../atl-mfc-shared/reference/cstringt-class.md). Indica el número máximo de caracteres que puede contener el control.  
  
- **Valor mínimo**

   Solo disponible cuando el tipo de variable es **BOOL**, `int`, **UINT**, **long**, `DWORD`, **float**, **double**, **BYTE**, **short**, [COLECurrency](../mfc/reference/colecurrency-class.md) o [CTime](../atl-mfc-shared/reference/ctime-class.md). Indica el valor mínimo aceptable para una escala o intervalo de fechas.  
  
- **Valor máximo**

   Solo disponible cuando el tipo de variable es **BOOL**, `int`, **UINT**, **long**, `DWORD`, **float**, **double**, **BYTE**, **short**, `COLECurrency` o `CTime`. Indica el valor más alto aceptable para una escala o intervalo de fechas.  
  
- **Archivo .h**

   Para los controles ActiveX, cuyas variables miembro requieren una clase contenedora. Establece el nombre del archivo de encabezado al que se va a agregar la declaración de clase.  
  
- **Archivo .cpp**

   Para los controles ActiveX, cuyas variables miembro requieren una clase contenedora. Establece el nombre del archivo de implementación al que se va a agregar la declaración de clase.  
  
- **Comentario**

   Proporciona un comentario en el archivo de encabezado para la variable miembro.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)