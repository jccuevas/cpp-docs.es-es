---
title: Prácticas recomendadas de seguridad para C++ | Microsoft Docs
ms.custom: ''
ms.date: 05/08/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- securitybestpracticesVC
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6cb76b2802b1f582621e3e0bacb565a974894d75
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693350"
---
# <a name="security-best-practices-for-c"></a>Procedimientos recomendados para la seguridad en C++

Este artículo contiene información sobre las herramientas y las prácticas de seguridad. Su uso no hace que las aplicaciones sean inmunes a los ataques, pero sí menos vulnerables.  
  
## <a name="visual-c-security-features"></a>Características de seguridad de Visual C++

 Estas características de seguridad están integradas en el compilador y el vinculador de Visual C++:  
  
 [/guard (Habilitar Protección de flujo de control)](../build/reference/guard-enable-control-flow-guard.md)  
 Hace que el compilador analice el flujo de control para destinos de llamada indirecta en tiempo de compilación y, a continuación, inserte código para comprobar los destinos en tiempo de ejecución.  
  
 [/GS (Comprobación de seguridad del búfer)](../build/reference/gs-buffer-security-check.md)  
 Indica al compilador que inserte código de detección de saturación en las funciones que presentan algún riesgo de seguridad. Cuando se detecta una saturación, se detiene la ejecución. Esta opción está activada de forma predeterminada.  
  
 [/SAFESEH (La imagen tiene controladores de excepciones seguros)](../build/reference/safeseh-image-has-safe-exception-handlers.md)  
 Indica al vinculador que incluya en la imagen de salida una tabla que contenga la dirección de cada controlador de excepciones. En tiempo de ejecución, el sistema operativo utiliza esta tabla para asegurarse de que solo se ejecutan controladores de excepciones legítimos. Esto ayuda a impedir la ejecución de controladores de excepciones incluidos por un ataque malintencionado en tiempo de ejecución. Esta opción está desactivada de forma predeterminada.  
  
 [/ NXCOMPAT](../build/reference/nxcompat.md), [/NXCOMPAT (Compatible con la prevención de ejecución de datos)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md)  
 Estas opciones del compilador y el vinculador habilitan la compatibilidad con la Prevención de ejecución de datos (DEP). DEP protege la CPU frente a la ejecución de páginas que no son de códigos.  
  
 [/analyze (Análisis de código)](../build/reference/analyze-code-analysis.md)  
 Esta opción del compilador activa el análisis de código que informa de posibles problemas de seguridad como saturaciones del búfer, memoria no inicializada, desreferenciación del puntero null y pérdidas de memoria. Esta opción está desactivada de forma predeterminada. Para obtener más información, consulte [análisis de código para C/C ++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
 [/DYNAMICBASE (Usar selección aleatoria del diseño del espacio de direcciones)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)  
 Esta opción del vinculador permite compilar una imagen ejecutable que se puede cargar en diferentes ubicaciones de la memoria al comienzo de la ejecución. Esta opción también hace que la ubicación de la pila en la memoria sea menos predecible.  
  
## <a name="security-enhanced-crt"></a>CRT con seguridad mejorada  
 La Biblioteca en tiempo de ejecución de C (CRT) se ha ampliado para incluir versiones seguras de funciones que presentan riesgos de seguridad; por ejemplo, la función de copia de cadena `strcpy` no comprobada. Puesto que las versiones anteriores no seguras de estas funciones están desusadas, producen advertencias en tiempo de compilación. Se recomienda usar las versiones seguras de estas funciones CRT en lugar de suprimir las advertencias de compilación. Para obtener más información, consulta [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="safeint-library"></a>Biblioteca SafeInt  
 [Biblioteca SafeInt](../windows/safeint-library.md) ayuda a evita desbordamientos de enteros y otros errores explotables que se podrían producir cuando la aplicación realiza operaciones matemáticas. El `SafeInt` biblioteca incluye el [clase SafeInt](../windows/safeint-class.md), [SafeIntException (clase)](../windows/safeintexception-class.md)y varias [SafeInt (funciones)](../windows/safeint-functions.md).  
  
 La clase `SafeInt` protege ante el desbordamiento de enteros y los ataques de división por cero. Puede utilizarla para controlar las comparaciones entre valores de tipos diferentes. Proporciona dos directivas de control de errores. La directiva predeterminada es para que la clase `SafeInt` produzca una excepción de clase `SafeIntException` que indique por qué no se puede completar una operación matemática. La segunda directiva es para que la clase `SafeInt` detenga la ejecución de programas. También puede definir una directiva personalizada.  
  
 Cada función `SafeInt` protege una operación matemática ante un error explotable. Se pueden utilizar dos clases diferentes de parámetros sin convertirlos a mismo tipo. Para proteger varias operaciones matemáticas, utilice la clase `SafeInt`.  
  
## <a name="checked-iterators"></a>Iteradores comprobados  
 Un iterador comprobado aplica límites de contenedor. De forma predeterminada, cuando un iterador comprobado está fuera de los límites, genera una excepción y finaliza la ejecución de programas. Un iterador comprobado proporciona otros niveles de respuesta que dependen de los valores que se asignan al preprocesador se define como  **\_SECURE\_SCL\_produce** y  **\_ITERADOR\_depurar\_nivel**. Por ejemplo, en  **\_ITERADOR\_depurar\_LEVEL = 2**, un iterador comprobado proporciona comprobaciones de corrección completa en modo de depuración que se hacen disponibles mediante aserciones. Para obtener más información, consulte [iteradores comprobados](../standard-library/checked-iterators.md) y [ \_ITERADOR\_depurar\_nivel](../standard-library/iterator-debug-level.md).  
  
## <a name="code-analysis-for-managed-code"></a>Análisis de código para código administrado  
 Análisis de código para código administrado, también conocido como FxCop, comprueba si los ensamblados cumplen las instrucciones de diseño de .NET Framework. FxCop analiza el código y los metadatos de cada ensamblado para comprobar si hay defectos en las áreas siguientes:  
  
-   Diseño de la biblioteca  
  
-   Localización  
  
-   Convenciones de nomenclatura  
  
-   Rendimiento  
  
-   Seguridad  
  
## <a name="windows-application-verifier"></a>Comprobador de aplicaciones para Windows  
 El [Application Verifier (AppVerifier)](/windows-hardware/drivers/debugger/application-verifier
) puede ayudar a identificar posibles problemas de compatibilidad, estabilidad y seguridad de la aplicación.  
  
 AppVerifier supervisa cómo una aplicación utiliza el sistema operativo. Inspecciona el sistema de archivos, el Registro, la memoria y las API mientras se ejecuta la aplicación, y recomienda correcciones del código fuente para los problemas que detecta.  
  
 Se puede utilizar AppVerifier para:  
  
-   Comprobar posibles errores de compatibilidad de aplicaciones producidos por errores de programación frecuentes.  
  
-   Examinar una aplicación para ver si tiene problemas relacionados con la memoria.  

-   Identificar los problemas de seguridad potenciales de una aplicación.  
  

## <a name="windows-user-accounts"></a>Cuentas de usuario de Windows  
 El uso de cuentas de usuario de Windows que pertenecen al grupo Administradores expone a los desarrolladores (y, por extensión, a los clientes) a riesgos de seguridad. Para obtener más información, consulte [que se ejecuta como un miembro del grupo de usuarios](running-as-a-member-of-the-users-group.md) y [usuario cómo Control de cuentas (UAC) afecta a la aplicación](how-user-account-control-uac-affects-your-application.md).

## <a name="guidance-for-speculative-execution-side-channels"></a>Guía para los canales del lado de ejecución especulativa

Para obtener información acerca de cómo identificar y mitigar vulnerabilidades de hardware de canal de lado de ejecución especulativa en software de C++, vea [instrucciones para desarrolladores de C++ para los canales del lado de ejecución especulativa](developer-guidance-speculative-execution.md).

## <a name="see-also"></a>Vea también  
<xref:System.Security>   
[Seguridad](/dotnet/standard/security/index)   
[Cómo el Control de cuentas de usuario (UAC) afecta a la aplicación](how-user-account-control-uac-affects-your-application.md)