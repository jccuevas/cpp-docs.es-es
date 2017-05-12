---
title: "Tipos fundamentales (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
caps.latest.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 14
---
# Tipos fundamentales (C++/CX)
Además de los tipos integrados de C\+\+ estándar, [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) admite el sistema de tipos definido por la arquitectura de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] ofreciendo typedefs para los tipos fundamentales de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] que se asignan a los tipos de C\+\+ estándar.[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] implementa tipos fundamentales numéricos, de caracteres y booleanos. Estas typedefs se definen en el el espacio de nombres `default`, que nunca debe especificarse de manera explícita. Además, [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] ofrece contenedores e implementaciones concretas para determinados tipos e interfaces de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].  
  
## Tipos de caracteres y booleanos  
 En la tabla siguiente se muestran los tipos de caracteres y booleanos integrados, y sus equivalentes de C\+\+ estándar.  
  
|Espacio de nombres|Nombre [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]|Definición|Nombre de C\+\+ estándar|Intervalo de valores|  
|------------------------|-------------------------------------------------------------------------|----------------|------------------------------|--------------------------|  
|Plataforma|Booleano|Un valor booleano de 8 bits.|bool|`true` \(distinto de cero\) y `false` \(cero\)|  
|default|char16|Valor no numérico de 16 bits que representa un punto de código Unicode \(UTF\-16\).|wchar\_t<br /><br /> O bien<br /><br /> L'c'|\(Especificado por el estándar Unicode\)|  
  
## Tipos numéricos  
 En la tabla siguiente se muestran los tipos numéricos integrados. Los tipos numéricos se declaran en el espacio de nombres `default` y son typedefs para el tipo integrado de C\+\+ correspondiente. No se admiten todos los tipos integrados de C\+\+ \(por ejemplo, long\) en [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. Para lograr coherencia y claridad, se recomienda que use el nombre [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)].  
  
|Nombre [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]|Definición|Nombre de C\+\+ estándar|Intervalo de valores|  
|-------------------------------------------------------------------------|----------------|------------------------------|--------------------------|  
|int8|Valor numérico con signo de 8 bits.|signed char|De –128 a 127|  
|uint8|Valor numérico sin signo de 8 bits.|unsigned char|De {0} a 255|  
|int16|Entero de 16 bits con signo.|short|De –32.768 a 32.767|  
|uint16|Entero de 16 bits sin signo.|unsigned short|De 0 a 65.535|  
|int32|Entero de 32 bits con signo.|int|De –2.147.483.648 a 2.147.483.647|  
|uint32|Entero de 32 bits sin signo.|unsigned int|De 0 a 4.294.967.295|  
|int64|Entero de 64 bits con signo.|long long \- o \- \_\_int64|De –9.223.372.036.854.775.808 a 9.223.372.036.854.775.807|  
|uint64|Entero de 64 bits sin signo.|long long sin firma \-o\- \_\_int64 sin firma|De 0 a 18.446.744.073.709.551.615|  
|float32|Número de punto flotante de 32 bits conforme a IEEE 754.|float|3,4E \+\/\- 38 \(7 dígitos\)|  
|float64|Número de punto flotante de 64 bits conforme a IEEE 754.|double|1,7E \+\/\- 308 \(15 dígitos\)|  
  
## Tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]  
 En la tabla siguiente se muestran algunos otros tipos definidos por la arquitectura de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] y están integrados en [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]. Object y String son tipos de referencia. Los demás son tipos de valores. Todos estos tipos se declaran en el espacio de nombres `Platform`. Para una lista completa, vea [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md).  
  
|Nombre|Definición|  
|------------|----------------|  
|Objeto|Representa cualquier tipo [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].|  
|String|Serie de caracteres que representan texto.|  
|Rect|Conjunto de cuatro números de punto flotante que representan la posición y el tamaño de un rectángulo.|  
|SizeT|Par ordenado de números de punto flotante que especifican un alto y un ancho.|  
|Punto|Par ordenado de coordenadas x de punto flotante y coordenadas y que definen un punto en un plano bidimensional.|  
|Guid|Valor no numérico de 128 bits que se usa como identificador único.|  
|UIntPtr|\(Solo para uso interno.\) Valor de 64 bits sin signo que se usa como puntero.|  
|IntPtr|\(Solo para uso interno.\)  Valor de 64 bits con signo que se usa como puntero.|  
  
## Vea también  
 [Sistema de tipos](../cppcx/type-system-c-cx.md)