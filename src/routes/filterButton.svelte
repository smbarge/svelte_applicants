<script lang="ts">
	/**
    Main component for handling the filter and columns buttons across all tables 
   
    Props:
        @prop {"columnPopup | filterPopup"} target - Defines if the button should be a column or filter button
        @prop {string} title - Name to be diplayed on the button

    Unused code: 
            <!-- {$_('exchanges.filters_button')} --> 
    */
	import { popup } from '@skeletonlabs/skeleton';

	import { ListBox, ListBoxItem } from '@skeletonlabs/skeleton';

    // Props 
	export let target: 'columnPopup' | 'filterPopup';
    export let title: string = "Placeholder"

	import { SlideToggle } from '@skeletonlabs/skeleton';


	let filterPopup  = {
		event: 'click',
		target: target,
		placement: 'bottom'
	};
</script>

<button
	class="btn flex flex-row justify-start btn-sm min-w-[45px]  rounded-md border-2 dark:border-surface-600 border-[#EDF1F7] !text-base md:px-4 h-11 "
	use:popup={filterPopup}
>
	<span class="   stroke-[#6C6C85] dark:stroke-slate-300">
		<!-- <FilterIcon /> -->
		{#if target ==='filterPopup'}
		<svg width="19" height="15" viewBox="0 0 19 15" fill="none" xmlns="http://www.w3.org/2000/svg">
			<path fill-rule="evenodd" clip-rule="evenodd" d="M14.5885 3.229C14.5885 4.99804 13.1544 6.43213 11.3853 6.43213C9.6163 6.43213 8.18221 4.99804 8.18221 3.229C8.18221 1.45997 9.6163 0.0258789 11.3853 0.0258789C13.1544 0.0258789 14.5885 1.45997 14.5885 3.229ZM11.3853 5.15088C12.4468 5.15088 13.3072 4.29043 13.3072 3.229C13.3072 2.16758 12.4468 1.30713 11.3853 1.30713C10.3239 1.30713 9.46346 2.16758 9.46346 3.229C9.46346 4.29043 10.3239 5.15088 11.3853 5.15088Z" fill="#4A5F7E"/>
			<path fill-rule="evenodd" clip-rule="evenodd" d="M3.91138 11.7707C3.91138 13.5397 5.34547 14.9738 7.1145 14.9738C8.88354 14.9738 10.3176 13.5397 10.3176 11.7707C10.3176 10.0016 8.88354 8.56755 7.1145 8.56755C5.34547 8.56755 3.91138 10.0016 3.91138 11.7707ZM7.1145 13.6925C6.05308 13.6925 5.19263 12.8321 5.19263 11.7707C5.19263 10.7092 6.05308 9.8488 7.1145 9.8488C8.17593 9.8488 9.03638 10.7092 9.03638 11.7707C9.03638 12.8321 8.17593 13.6925 7.1145 13.6925Z" fill="#4A5F7E"/>
			<path d="M11.1718 11.7352C11.1718 11.3814 11.4586 11.0946 11.8124 11.0946H17.7916C18.1454 11.0946 18.4322 11.3814 18.4322 11.7352C18.4322 12.089 18.1454 12.3759 17.7916 12.3759H11.8124C11.4586 12.3759 11.1718 12.089 11.1718 11.7352Z" fill="#4A5F7E"/>
			<path d="M6.68742 2.55295C7.04123 2.55295 7.32804 2.83977 7.32804 3.19357C7.32804 3.54738 7.04123 3.8342 6.68742 3.8342L0.708252 3.8342C0.354444 3.8342 0.067627 3.54738 0.067627 3.19357C0.067627 2.83977 0.354444 2.55295 0.708252 2.55295L6.68742 2.55295Z" fill="#4A5F7E"/>
			<path d="M0.067627 11.7352C0.067627 11.3814 0.354445 11.0946 0.708252 11.0946H2.41659C2.77039 11.0946 3.05721 11.3814 3.05721 11.7352C3.05721 12.089 2.77039 12.3759 2.41659 12.3759H0.708252C0.354445 12.3759 0.067627 12.089 0.067627 11.7352Z" fill="#4A5F7E"/>
			<path d="M17.7916 2.55295C18.1454 2.55295 18.4322 2.83977 18.4322 3.19357C18.4322 3.54738 18.1454 3.8342 17.7916 3.8342H16.0833C15.7294 3.8342 15.4426 3.54738 15.4426 3.19357C15.4426 2.83977 15.7294 2.55295 16.0833 2.55295H17.7916Z" fill="#4A5F7E"/>
			</svg>
{:else}
			<svg width="18" height="17" viewBox="0 0 18 17" fill="none" xmlns="http://www.w3.org/2000/svg">
				<path d="M6.28894 1.6665V15.3332M11.7556 1.6665V15.3332M1.84727 15.3332H16.1973C16.7631 15.3332 17.2223 14.874 17.2223 14.3082V2.69151C17.2223 2.12571 16.7631 1.6665 16.1973 1.6665H1.84727C1.28147 1.6665 0.822266 2.12571 0.822266 2.69151V14.3082C0.822266 14.874 1.28147 15.3332 1.84727 15.3332Z"  stroke-width="1.36667" stroke-linecap="round" stroke-linejoin="round"/>
				</svg>
				{/if}
	</span>
	<span class="font-sans !text-[#6C6C85]">
        {title}
	</span>
</button>



<div class="card shadow-xl py-2 z-40" data-popup="filterPopup">
	<ListBox rounded="rounded-none">
		<ListBoxItem name="medium"  value="books">
			<svelte:fragment slot="lead">
				<label class="flex items-center space-x-2">
					<input class="checkbox" type="checkbox" checked />
					<p>Non KYC</p>
				</label>
			</svelte:fragment>
		
		</ListBoxItem>
	</ListBox>
	<ListBox rounded="rounded-none">
		<ListBoxItem name="medium"  value="books">
			<svelte:fragment slot="lead">
				<label class="flex items-center space-x-2">
					<input class="checkbox" type="checkbox" checked />
					<p>Non KYC</p>
				</label>
				
			</svelte:fragment>
			
		</ListBoxItem>
	</ListBox>
	<ListBox rounded="rounded-none">
		<ListBoxItem name="medium"  value="books">
			<svelte:fragment slot="lead">
				<label class="flex items-center space-x-2">
					<input class="checkbox" type="checkbox" checked />
					<p>Non KYC</p>
				</label>
			</svelte:fragment>
			
		</ListBoxItem>
	</ListBox>
	<div class="arrow bg-surface-100-800-token" />
</div>

<div class="card shadow-xl py-1 z-40" data-popup="columnPopup">
	<ListBox rounded="rounded-none">
		<ListBoxItem name="medium"  value="books">
			<svelte:fragment slot="lead">
				<label class="flex items-center space-x-2">
					<input class="checkbox h-5 w-5" type="checkbox" checked />
					<p>Non KYC</p>
				</label>
			</svelte:fragment>
			
		</ListBoxItem>
	</ListBox>
	<div class="arrow bg-surface-100-800-token" />
</div>
