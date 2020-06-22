---
id: Usage.Decorator
title: The Decorator Syntax of React Native Sensors
sidebar_label: Decorator Syntax
---

```javascript
import React, { Component } from "react";
import { Text, View } from "react-native";
import { decorator as sensors } from "react-native-sensors";

class MyComponent {
	// no lifecycle needed
	render() {
		const { sensorsFound, Accelerometer, Gyroscope } = this.props;

		if (!Accelerometer || !Gyroscope) {
			// One of the sensors is still initializing
			return null;
		}

		return (
			<View style={styles.container}>
				<Text style={styles.welcome}>
					{(sensorsFound["Accelerometer"] &&
						`Acceleration has value: ${Accelerometer}`) ||
						"Acceleration is not available"}
					{(sensorsFound["Gyroscope"] && `Gyro has value: ${Gyroscope}`) ||
						"Gyro is not available"}
				</Text>
			</View>
		);
	}
}

export default sensors({
	Accelerometer: {
		updateInterval: 300 // optional
	},
	Gyroscope: true
})(MyComponent);
```
