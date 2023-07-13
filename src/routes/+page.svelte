<script lang="ts">
	import { Button } from '$components/ui/button';
	import {
		Card,
		CardContent,
		CardDescription,
		CardFooter,
		CardHeader,
		CardTitle
	} from '$components/ui/card';
	import { Input } from '$components/ui/input';
	import { Label } from '$components/ui/label';
	import { Tabs, TabsContent, TabsList, TabsTrigger } from '$components/ui/tabs';

	let activeTab = 'login'; // Add a reactive variable for the active tab

	const handleTabChange = (tab: string) => {
		console.log(tab);
		console.log('hello');

		activeTab = tab; // Update the active tab based on the selected tab
	};

	const handleThis = (event: CustomEvent<string>) => {
		const { detail } = event;
		const tabValue: string = detail;

		console.log(tabValue);
		// Perform any additional actions based on the current tab value
	};
</script>

<div class="bg-blue-200 flex justify-center items-center h-screen select-none">
	<Card class="p-1 h-fit rounded-2xl w-[400px]">
		<CardHeader class="text-center">
			<CardTitle class="text-2xl">{activeTab === 'login' ? 'Login' : 'Signup'}</CardTitle>
			<!-- Update CardTitle based on the active tab -->
		</CardHeader>
		<CardContent>
			<Tabs bind:value={activeTab} class="space-y-5">
				<TabsList class="grid w-full grid-cols-2 rounded-2xl">
					<TabsTrigger value="login" class="rounded-2xl" on:click={() => handleTabChange('login')}>
						Login
					</TabsTrigger>
					<TabsTrigger
						value="signup"
						class="rounded-2xl"
						on:click={() => handleTabChange('signup')}
					>
						Signup
					</TabsTrigger>
				</TabsList>
				<TabsContent value="login" class="flex flex-col">
					<Input id="user_email" type="email" placeholder="Email" class="mb-3 rounded-2xl" />
					<Input
						id="user_password"
						type="password"
						placeholder="Password"
						class="mb-5 rounded-2xl"
					/>
					<!-- <Input id="user_password" type="password" placeholder="Password" class="mb-1" />
					<p class="text-xs mb-5">Forgot Password?</p> -->
					<Button class="font-semibold rounded-2xl">Login</Button>
				</TabsContent>
				<TabsContent value="signup" class="flex flex-col">
					<Input
						id="email_address"
						type="email"
						placeholder="Email Address"
						class="mb-3 rounded-2xl"
					/>
					<Input id="password" type="password" placeholder="Password" class="mb-3 rounded-2xl" />
					<Input
						id="confirm-password"
						type="password"
						placeholder="Confirm Password"
						class="mb-5 rounded-2xl"
					/>
					<Button class="font-semibold rounded-2xl">Signup</Button>
				</TabsContent>
			</Tabs>
		</CardContent>
	</Card>
</div>
