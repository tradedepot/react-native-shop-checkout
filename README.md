
# react-native-shop-checkout

## Getting started

`$ npm install react-native-shop-checkout --save`

### Mostly automatic installation

`$ react-native link react-native-shop-checkout`

### Manual installation


#### Android

1. Open up `android/app/src/main/java/[...]/MainActivity.java`
  - Add `import com.tradedepot.react.shopagent.RNAgentCheckoutPackage;` to the imports at the top of the file
  - Add `new RNAgentCheckoutPackage()` to the list returned by the `getPackages()` method
2. Append the following lines to `android/settings.gradle`:
  	```
  	include ':react-native-shop-checkout'
  	project(':react-native-shop-checkout').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-shop-checkout/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
  	```
      implementation project(':react-native-shop-checkout')
  	```

4. add shoptop checkout sdk to app/build.gradle
   ```
	implementation('co.tradedepot.shop.sdk:checkout:0.0.1+4@aar') {
        transitive = true
    }
   ```
5. Config for Android (intercom-android)
   - In `android/app/src/main/java/com/YOUR_APP/app/MainApplication.java`, add the following code in the respective sections of the file using your shopCheckout Android API Key and shopCheckout Api Key
   ```
		// ...other configuration here...

		import co.tradedepot.shop.sdk.checkout.Checkout;

		public class MainApplication extends Application {

			@Override
			public void onCreate() {
				super.onCreate();
				Checkout.initialize(this, "API_KEY");

				// ...other configuration here...

			}
		}
	```
	- In ` android/build.gradle add   maven { url  "https://dl.bintray.com/tradedepot/agent-checkout-sdk-android" }`
	```
		allprojects {
			repositories {

				//...other configuration here...

				maven { url  "https://dl.bintray.com/tradedepot/agent-checkout-sdk-android" }
			}
		}
	```
   - Open android manifest set the allowbackup to true
	```
		<application
		// ...other configuration here...
		android:allowBackup="true" ---> here
		>
	```



## Usage 
Import the Module
```javascript
import shopCheckout from 'react-native-shop-checkout';
```

  Register a shoptopUp Checkout 

  ```
shopCheckout.register({
	// Pre-defined user attributes
	agentId: 'fhj50tgoonoo',
	firstName: 'chisom',
	lastName: 'onwuegbuzie',
	phoneNumber: '+2348066379681',
	countryCode: 'NG',
	company: 'Goldtek Ventures',
	latitude: 3.134555,
	longitude: 3.058585,
	address: '259 etim inyang crescent'
});
```
Open Products
```
shopCheckout.openProducts();
```
Open Transaction
```
shopCheckout.openTransaction();
```
Logout
```
shopCheckout.logout();
```
