---
layout: post
title: Atmega328p Microcontroller ADC
date: 2018-07-22 00:00:00 +0500
description: Simple project about Analog-to-Digital Conversion using Atmega328p # Add post description (optional)
img: microcontroller_title.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Microcontroller, Atmega328p, Atmel Studio, ADC]
---


This is a simple project to use Analog-to-Digital Converter (ADC) on Atmega328p (Arduino UNO), so for this example it will be used a Sensing Force, 
 it is opmized for use in human touch control of electronic devices such as automotive electronics, medical systems, and in industrial and robotics applications.

The Atmega328p <a href="https://www.sparkfun.com/datasheets/Components/SMD/ATMega328.pdf">DataSheet</a> that will be used to develop the code.


## Component - Sensing Force

the component used was the FSR 402 model is a single-zone Force Sensing Resistor which is a Force Sensing that
  provides an inverse change in resistance in response to an increase/decrease in applied force.

![Microcontroller]({{site.baseurl}}/assets/img/microcontroler_component.jpg){:height="450px" width="45%" style="display: block; margin: 0 auto"}


## Code


<b>The initialization ADC function </b>
{% highlight C++ %}

void InitADC()
{
	// Select Vref=AVcc (5v)
	ADMUX |= (1<<REFS0);
	//set prescaler to 128 and enable ADC
	ADCSRA |= (1<<ADPS2)|(1<<ADPS1)|(1<<ADPS0)|(1<<ADEN);
}
{% endhighlight %}


<b>Read ADC function </b>
{% highlight C++ %}

uint16_t ReadADC(uint8_t ADCchannel)
{
	//select ADC channel with safety mask
	ADMUX = (ADMUX & 0xF0) | (ADCchannel & 0x0F);
	//single conversion mode
	ADCSRA |= (1<<ADSC);
	// wait until ADC conversion is complete
	while( ADCSRA & (1<<ADSC) );
	return ADC;
}
{% endhighlight %}


<b>initialization Ports </b>
{% highlight C++ %}
DDRC &= ~(1<<DDC0); //Set PORTC0 as input
	DDRB |= (1<<DDB5);	//Set PORTB5 as output
	DDRB |= (1<<DDB4);	//Set PORTB4 as output
	
	InitADC();
{% endhighlight %}

<b>Read ADC function </b>
{% highlight C++ %}
adc_res=ReadADC(0)	;
		
		if(adc_res > 1022){
			PORTB |= (1<<PORTB5) ;  // toggle LED
		}
		if(adc_res > 512){
			
			PORTB |= (1<<PORTB4) ; 
		}

{% endhighlight %}




