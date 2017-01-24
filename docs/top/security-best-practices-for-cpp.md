---
title: "Procedimientos recomendados para la seguridad en C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "securitybestpracticesVC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "seguridad [C++]"
  - "seguridad [C++], procedimientos recomendados"
  - "Visual C++, seguridad"
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
caps.latest.revision: 45
caps.handback.revision: 45
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Procedimientos recomendados para la seguridad en C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este artículo contiene información sobre las herramientas y las prácticas de seguridad.  Su uso no hace que las aplicaciones sean inmunes a los ataques, pero sí menos vulnerables.  
  
## Características de seguridad de Visual C\+\+  
 Estas características de seguridad están integradas en el compilador y el vinculador de Visual C\+\+:  
  
 [\/guard \(habilitar Protección de flujo de control\)](../build/reference/guard-enable-control-flow-guard.md)  
 Hace que el compilador analice el flujo de control para los destinos de llamada indirecta en tiempo de compilación y que después inserte código para comprobar los destinos en tiempo de ejecución.  
  
 [\/GS \(Comprobación de seguridad del búfer\)](../build/reference/gs-buffer-security-check.md)  
 Indica al compilador que inserte código de detección de saturación en las funciones que presentan algún riesgo de seguridad.  Cuando se detecta una saturación, se detiene la ejecución.  Esta opción está activada de forma predeterminada.  
  
 [\/SAFESEH \(La imagen tiene controladores de excepciones seguros\)](../build/reference/safeseh-image-has-safe-exception-handlers.md)  
 Indica al vinculador que incluya en la imagen de salida una tabla que contenga la dirección de cada controlador de excepciones.  En tiempo de ejecución, el sistema operativo utiliza esta tabla para asegurarse de que solo se ejecutan controladores de excepciones legítimos.  Esto ayuda a impedir la ejecución de controladores de excepciones incluidos por un ataque malintencionado en tiempo de ejecución.  Esta opción está desactivada de forma predeterminada.  
  
 [\/NXCOMPAT](../build/reference/nxcompat.md), [\/NXCOMPAT \(compatible con la prevención de ejecución de datos\)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md)  
 Estas opciones del compilador y el vinculador habilitan la compatibilidad con la Prevención de ejecución de datos \(DEP\).  DEP protege la CPU frente a la ejecución de páginas que no son de códigos.  
  
 [\/analyze \(análisis de código\)](../build/reference/analyze-code-analysis.md)  
 Esta opción del compilador activa el análisis de código que informa de posibles problemas de seguridad como saturaciones del búfer, memoria no inicializada, desreferenciación del puntero null y pérdidas de memoria.  Esta opción está desactivada de forma predeterminada.  Para obtener más información, vea [Análisis de código para obtener información general de C\/C\+\+](../Topic/Code%20Analysis%20for%20C-C++%20Overview.md).  
  
 [\/DYNAMICBASE \(Usar selección aleatoria del diseño del espacio de direcciones\)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)  
 Esta opción del vinculador permite compilar una imagen ejecutable que se puede cargar en diferentes ubicaciones de la memoria al comienzo de la ejecución.  Esta opción también hace que la ubicación de la pila en la memoria sea menos predecible.  
  
## CRT con seguridad mejorada  
 La Biblioteca en tiempo de ejecución de C \(CRT\) se ha ampliado para incluir versiones seguras de funciones que presentan riesgos de seguridad; por ejemplo, la función de copia de cadena `strcpy` no comprobada.  Puesto que las versiones anteriores no seguras de estas funciones están desusadas, producen advertencias en tiempo de compilación.  Se recomienda usar las versiones seguras de estas funciones CRT en lugar de suprimir las advertencias de compilación.  Para obtener más información, consulte [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md).  
  
## Biblioteca SafeInt  
 [SafeInt \(Biblioteca\)](../windows/safeint-library.md) ayuda a evitar los desbordamientos de enteros y otros errores explotables que se podrían producir cuando la aplicación realiza operaciones matemáticas.  La biblioteca `SafeInt` incluye la [SafeInt \(Clase\)](../windows/safeint-class.md), la [SafeIntException \(Clase\)](../windows/safeintexception-class.md) y varias [SafeInt \(Funciones\)](../windows/safeint-functions.md).  
  
 La clase `SafeInt` protege ante el desbordamiento de enteros y los ataques de división por cero.  Puede utilizarla para controlar las comparaciones entre valores de tipos diferentes.  I proporciona dos directivas de control de errores.  La directiva predeterminada es para que la clase `SafeInt` produzca una excepción de clase `SafeIntException` que indique por qué no se puede completar una operación matemática.  La segunda directiva es para que la clase `SafeInt` detenga la ejecución de programas.  También puede definir una directiva personalizada.  
  
 Cada función `SafeInt` protege una operación matemática ante un error explotable.  Se pueden utilizar dos clases diferentes de parámetros sin convertirlos a mismo tipo.  Para proteger varias operaciones matemáticas, utilice la clase `SafeInt`.  
  
## Iteradores comprobados  
 Un iterador comprobado aplica límites de contenedor.  De forma predeterminada, cuando un iterador comprobado está fuera de los límites, genera una excepción y finaliza la ejecución de programas.  Un iterador comprobado proporciona otros niveles de respuesta que dependen de valores asignados a definiciones del preprocesador como **\_SECURE\_SCL\_THROWS** y **\_ITERATOR\_DEBUG\_LEVEL**.  Por ejemplo, en **\_ITERATOR\_DEBUG\_LEVEL\=2**, un iterador comprobado proporciona comprobaciones de corrección completa en modo de depuración, que están disponibles mediante aserciones.  Para obtener más información, vea [Iteradores activados](../standard-library/checked-iterators.md).  
  
## Análisis de código para código administrado  
 Análisis de código para código administrado, también conocido como FxCop, comprueba si los ensamblados cumplen las instrucciones de diseño de .NET Framework.  FxCop analiza el código y los metadatos de cada ensamblado para comprobar si hay defectos en las áreas siguientes:  
  
-   Diseño de la biblioteca  
  
-   Localización  
  
-   Convenciones de nomenclatura  
  
-   Rendimiento  
  
-   Seguridad  
  
## Comprobador de aplicaciones para Windows  
 Application Verifier \(AppVerifier\) puede ayudar a identificar posibles problemas de compatibilidad de aplicaciones, estabilidad y seguridad.  
  
 AppVerifier supervisa cómo una aplicación utiliza el sistema operativo.  Inspecciona el sistema de archivos, el Registro, la memoria y las API mientras se ejecuta la aplicación, y recomienda correcciones del código fuente para los problemas que detecta.  
  
 Se puede utilizar AppVerifier para:  
  
-   Comprobar posibles errores de compatibilidad de aplicaciones producidos por errores de programación frecuentes.  
  
-   Examinar una aplicación para ver si tiene problemas relacionados con la memoria.  
  
-   Identificar los problemas de seguridad potenciales de una aplicación.  
  
 AppVerifier forma parte del kit de herramientas de compatibilidad de aplicaciones, que está disponible en el sitio web de TechNet [Compatibilidad de las aplicaciones](http://go.microsoft.com/fwlink/?LinkId=91277).  
  
## Características de seguridad de .NET Framework  
 En [NIB: Configuring Security Policy](http://msdn.microsoft.com/es-es/0f130bcd-1bba-4346-b231-0bcca7dab1a4) se describen instrucciones y herramientas para ajustar las directivas de seguridad de .NET Framework.  
  
## Cuentas de usuario de Windows  
 El uso de cuentas de usuario de Windows que pertenecen al grupo Administradores expone a los desarrolladores \(y, por extensión, a los clientes\) a riesgos de seguridad.  Para obtener más información, consulte [Ejecutar como miembro del grupo de usuarios](../top/running-as-a-member-of-the-users-group.md) y [Cómo el Control de cuentas de usuario \(UAC\) afecta a la aplicación](../Topic/How%20User%20Account%20Control%20\(UAC\)%20Affects%20Your%20Application.md).  
  
## Vea también  
 <xref:System.Security>   
 [Security](../Topic/Security%20in%20the%20.NET%20Framework.md)   
 [Cómo el Control de cuentas de usuario \(UAC\) afecta a la aplicación](../Topic/How%20User%20Account%20Control%20\(UAC\)%20Affects%20Your%20Application.md)