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
		activeTab = tab; // Update the active tab based on the selected tab
	};
</script>

<div class="flex justify-center lg:justify-between items-center h-screen w-screen select-none">
	<div class="h-screen w-1/2 relative hidden lg:block">
		<img
			src="business-image.jpg"
			alt="Background"
			class="absolute inset-0 w-full h-full object-cover"
		/>
		<div class="absolute inset-0 bg-purple-600 opacity-30" />
		<div class="absolute bottom-0 left-0 p-2 text-white text-xs">
			Photo by <a
				href="https://unsplash.com/ja/@ryoji__iwata?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
				class="font-semibold">Ryoji Iwata</a
			>
			on
			<a
				href="https://unsplash.com/s/photos/business?orientation=portrait&utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
				class="font-semibold">Unsplash</a
			>
		</div>
	</div>

	<div class="flex justify-center items-center h-screen w-1/2">
		<div class="relative">
			<div
				class="absolute inset-0 bg-gradient-to-r from-purple-100 to-purple-800 transform -rotate-12 ml-2 rounded-2xl"
			/>

			<Card class="p-1 h-fit rounded-2xl w-[400px] drop-shadow-lg relative z-10">
				<CardHeader class="text-center">
					<CardTitle class="text-2xl">{activeTab === 'login' ? 'Login' : 'Signup'}</CardTitle>
					<!-- Update CardTitle based on the active tab -->
				</CardHeader>
				<CardContent>
					<Tabs bind:value={activeTab} class="space-y-5">
						<TabsList class="grid w-full grid-cols-2 rounded-2xl">
							<TabsTrigger
								value="login"
								class="rounded-2xl"
								on:click={() => handleTabChange('login')}
							>
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
							<Input
								id="password"
								type="password"
								placeholder="Password"
								class="mb-3 rounded-2xl"
							/>
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
	</div>
</div>
